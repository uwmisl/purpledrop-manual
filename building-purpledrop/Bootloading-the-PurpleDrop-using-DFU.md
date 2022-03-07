# Programming the PurpleDrop Embedded Software

The PurpleDrop software can be updated using the DFU bootloader. On the STM32 processor, this bootloader is built into the chip. On the SAMG55 processor (e.g. found on rev 6.4) the bootloader must first be programmed via SWD. In both cases, to enter bootloader mode, reset the PurpleDrop by pressing and releasing the reset button while holding the BOOT0 button. The processor should boot into bootloader mode, and should enumerate as a DFU USB device.

The .dfu file for programming can be obtained from the [purpledrop-stm32](https://github.com/uwmisl/purpledrop-stm32/releases) releases page.

## Programming from with dfu-util on Linux/MacOS/Windows

An open source DFU programming tool `dfu-util` is available, and will work with the PurpleDrop. Most linux distributions can install this tool as a package, e.g. on ubuntu, run `apt install dfu-util`. On Mac, it can be installed with homebrew: `brew install dfu-util`. There are windows binaries available, which can be used with some additional setup. See <http://dfu-util.sourceforge.net> for the latest instructions on installation. 

To program SAMG55 PurpleDrop, run `dfu-util -d 1209 -a 0 -D purpledrop-sam_vX.Y.Z.bin`.

To program STM32 PurpleDrop, run `dfu-util -a 0 -D purpledrop_vX.Y.Z.dfu`. 

You may need to run the `dfu-util` command as root, depending on the permissions set on your USB device. 

## Programming with the ST DFuSe program on Windows

ST provides a [DFuSe programming utility](https://www.st.com/en/development-tools/stsw-stm32080.html) for windows, that should work for programming the PurpleDrop from windows, and may provide a simpler user experience -- but this author has not yet attempted it.

## Checking the version of software installed

The embedded software can report it's own version over the USB port. To determine the currently programmed version, you can use the `pdcli info` command, provided by the [purpledrop python package](https://github.com/uwmisl/purpledrop-driver). Alternatively, the version of a connected device can be found in the browser UI, by holding the mouse cursor over the "information" icon next to the device connection status on the display.