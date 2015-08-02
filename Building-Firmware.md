The PortaPack has its own firmware. You may [use a prebuilt package](Updating-Firmware). If you prefer to build from scratch, here's how:

## Tools

You will need a few tools installed on your computer before you begin.

* [GCC-ARM-Embedded](https://launchpad.net/gcc-arm-embedded) - I am using the "4.9-2015-q2" release.
* [dfu-util](http://dfu-util.sourceforge.net) - Used to load and run the stock HackRF firmware from RAM.

## Getting the Source Code

The source code is hosted on GitHub. Change to a directory where you want the source code, and clone the source repository.

    git clone https://github.com/sharebrained/portapack-hackrf.git

Change directories into the cloned repository.

    cd portapack-hackrf

## Building

Change directories into the "firmware" subdirectory.

    cd firmware

Make the SPI flash binary image (which builds the bootstrap, application, and baseband binaries):

    make

Once you have built the binary, you must program it into the HackRF One SPI flash.

## Flashing

Plug the HackRF into a USB port on your computer.

Hold down the HackRF DFU button. Press and release the HackRF reset button. Then release the DFU button. The HackRF is now in DFU mode.

Program the HackRF's SPI flash:

    make program

When finished, press the reset button on the HackRF. The PortaPack code is now running from the SPI flash on the HackRF.

If using dfu-util 0.8 you will get an error. This is the workaround

    dfu-util --device 1fc9:000c --download hackrf_one_usb_ram.dfu --reset
    hackrf_spiflash -w portapack-h1-firmware.bin