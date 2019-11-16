The PortaPack has its own firmware. You may [use a prebuilt package](Updating-Firmware). If you prefer to build from scratch, here's how:

## Tools

You will need a few tools installed on your computer before you begin.

* [GCC-ARM-Embedded](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads) - I am using the "9-2019-q4-major" release.
* [CMake 2.8.9 or newer](https://cmake.org/download/) - Build system now uses CMake instead of GNU Make.
* [PyYAML](https://pyyaml.org/) for Python 2.7 (for libopencm3, built by hackrf submodule).
* [dfu-util 0.7 or newer](http://dfu-util.sourceforge.net) - Used to load and run the stock HackRF firmware from RAM.

## Getting the Source Code

The source code is hosted on GitHub. Change to a directory where you want the source code, and clone the source repository.

    git clone --recurse-submodules https://github.com/sharebrained/portapack-hackrf.git

Change directories into the cloned repository.

    cd portapack-hackrf

## Building

Make a "build" directory and initialize the CMake build files into that directory:

    mkdir build
    cd build
    cmake ..

Make the SPI flash binary image (which builds the bootstrap, application, and baseband binaries):

    make firmware

The binary will be at "firmware/portapack-h1-firmware.bin".

Once you have built the binary, you must program it into the HackRF One SPI flash.

## Flashing

Plug the HackRF into a USB port on your computer.

Hold down the HackRF DFU button. Press and release the HackRF reset button. Wait a second or two. Then release the DFU button. The HackRF is now in DFU mode.

Program the HackRF's SPI flash:

    make program

When finished, press the reset button on the HackRF. The PortaPack code is now running from the SPI flash on the HackRF.