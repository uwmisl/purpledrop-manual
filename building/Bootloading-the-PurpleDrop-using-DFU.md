# Programming the PurpleDrop Embedded Software

The PurpleDrop software can be updated using the DFU bootloader on the STM32 processor. To enter bootloader mode, reset the PurpleDrop while holding the BOOT0 button. The processor should boot into bootloader mode, and should enumerate as an ST Microelectronics DFU USB device.

The .dfu file for programming can be obtained from the [purpledrop-stm32](https://github.com/uwmisl/purpledrop-stm32/releases) releases page.

## Programming from with dfu-util on Linux/MacOS/Windows

An open source DFU programming tool `dfu-util` is available, and will work with the PurpleDrop. Most linux distributions can install this tool as a package, e.g. on ubuntu, run `apt install dfu-util`. On Mac, it can be installed with homebrew: `brew install dfu-util`. There are windows binaries available, which can be used with some additional setup. See <http://dfu-util.sourceforge.net> for the latest instructions on installation. 

To program PurpleDrop, run `dfu-util -a 0 -D purpledrop_vX.Y.Z.dfu`. You may need to run this command as root, depending on the permissions of your USB devices. 

## Programming with the ST DFuSe program on Windows

ST provides a [DFuSe programming utility](https://www.st.com/en/development-tools/stsw-stm32080.html) for windows, that should work for programming the PurpleDrop from windows, and may provide a simpler user experience -- but this author has not yet attempted it.

## Checking the version of software installed

The embedded software can report it's own version over the USB port. To determine the currently programmed version, you can use the `pdcli info` command, provided by the [purpledrop python package](https://github.com/uwmisl/purpledrop-driver).