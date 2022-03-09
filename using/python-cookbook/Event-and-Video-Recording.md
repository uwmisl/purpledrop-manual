Event and Video Recording
=========================

When running pdserver along with pdcam, the websocket server provides a stream
of messages which contain state updates and captured images. This can be captured
using the `pdrecord` command line utility, however it may be more useful to 
control the capture of data from within your own script. For exampe, in many
experiments there are brief periods of interest when things are being moved,
followed by long times when nothing is happening. Because the captured images
contain a lot of bytes, it is often better to record only the interesting 
parts for later examination. 

```{note}

The recordings are raw protobuf messages, as defined in the `purpledrop.protobuf.messages_pb2` module, 
which is generated from [these message definitions](https://github.com/uwmisl/purpledrop-driver/blob/master/protobuf/messages.proto).

The `pdlog` utility can extract an mpeg-4 video from a binary log. For example, if you have a log 
saved in `log.bin`:

`pdlog --video log.mp4 log.bin` will extract the video frames to `log.mp4`
```

```python
# event_recorder.py
import asyncio
import threading
import time
import struct
import websockets

class EventRecorder(object):
    def __init__(self, uri):
        """An EventRecorder captures the event stream from the purpledrop API server to a file
        
        When creating an EventRecorder, you must provide the URI to the purpledrop websocket 
        server. Typically, this is run on port 7001 of the Raspberry PI (or whever pdserver is
        run). The URI should use the `ws` protocol, for example: `ws://localhost:7001` is a
        typical websocket URI. 

        To start recording, call `recorder.start('logfile.bin`)`. To stop, call `recorder.stop()`. 

        Recording is run in a background thread.
        """
        self.uri = uri
        self.thread = threading.Thread(target=self.__thread_entry, daemon=True)
        self.start_event = None
        self.output_file = None
        self.stop_event = None
        self.loop = None
        self.init_event = threading.Event()
        self.thread.start()

    def start(self, filepath):
        """Start recording to the provided file"""
        # Make sure wait_for_start task has started
        self.init_event.wait(timeout=1.0)
        if self.output_file is not None:
            raise RuntimeError("Already recording. Call stop() first.")
        self.output_file = filepath
        self.loop.call_soon_threadsafe(self.start_event.set)

    def stop(self):
        """Stop in progress recording"""
        self.loop.call_soon_threadsafe(self.stop_event.set)
        if not self.thread.is_alive():
            raise RuntimeError("EventRecorder thread has terminated.")
        # Wait for capture to finish
        while self.output_file is not None:
            time.sleep(0.1)

    async def __record(self, filepath):
        msg_count = 0
        with open(filepath, 'wb') as f:
            # With default close timeout, it takes a long time to close.
            async with websockets.connect(self.uri, close_timeout=0.2) as ws:
                while True:
                    recv_task = asyncio.create_task(ws.recv())
                    stop_task = asyncio.create_task(self.stop_event.wait())
                    done, pending = await asyncio.wait({recv_task, stop_task}, return_when=asyncio.FIRST_COMPLETED)
                    if stop_task in done:
                        recv_task.cancel()
                        return msg_count

                    msg_count += 1
                    raw_event = recv_task.result()
                    length_bytes = struct.pack('I', len(raw_event))
                    f.write(length_bytes)
                    f.write(raw_event)

    async def __wait_for_start(self):
        self.start_event = asyncio.Event()
        self.stop_event = asyncio.Event()
        self.loop = asyncio.get_event_loop()
        self.init_event.set()
        while True:
            await self.start_event.wait()
            self.start_event.clear()
            msg_count = await self.__record(self.output_file)
            self.output_file = None
            self.stop_event.clear()

    def __thread_entry(self):
        asyncio.run(self.__wait_for_start())
```

And here's a quick example of using the event recorder to capture three separate logs at different times:

```python
# event_recorder_demo.py
from event_recorder import EventRecorder
import time

PD_HOST = "mcbride-purpledrop"

rec = EventRecorder(f'ws://{PD_HOST}:7001')

# Record three segments
for i in range(3):
    print("Starting capture {i}")
    # Start the recorder and let it capture for 10 seconds
    rec.start(f'log{i}.bin')
    time.sleep(10.0)
    print ("Stopping Capture")
    rec.stop()
    # Capture is now stopped. Wait 5 seconds before moving on to the next
    time.sleep(5.0)
```