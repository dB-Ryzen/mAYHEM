The PortaPack has its own firmware, which needs to be flashed into the HackRF One SPI flash. Until you program the HackRF with the PortaPack-enhanced firmware, the PortaPack display will be blank and the controls will be non-responsive.

Please note that you can't brick the HackRF, unless you physically damage the hardware somehow. The HackRF microcontroller contains ROM USB DFU bootloader code that can't be erased. So even if your firmware update goes horribly wrong, you will be able to reload code via this USB bootloader. For information on how to do this, see below: "Restoring HackRF Firmware".

## Tools

If you're using Windows, you get [your own set of instructions](Updating-Firmware-Windows)!

For Linux and Mac OS X users, you will need a few tools installed on your computer before you begin:

* [dfu-util](http://dfu-util.sourceforge.net) 0.8 or newer - Used to load and run the stock HackRF firmware from RAM. dfu-util 0.8 is recommended, as it is the most extensively tested with the HackRF hardware and build software.
* [hackrf](https://github.com/mossmann/hackrf) - All you need is the host tools, specifically, hackrf_spiflash.

## Getting the Firmware

Firmware is available three ways:

* Download a [released firmware package](https://github.com/sharebrained/portapack-hackrf/releases).
* Download a [continuous integration build of the latest firmware](http://munchkins.net/portapack/). ![Build Status](https://travis-ci.org/sharebrained/portapack-hackrf.svg?branch=master)
* [Build your own firmware](Building-Firmware).

## Flashing

If you downloaded the pre-built package, change directories to where you unzipped or un-tarred/un-bzipped the package.

If you built your own firmware, the files you need are in the firmware/ subdirectory of your local portapack-hackrf repository.

You will need two files: hackrf_one_usb.dfu, which is the stock HackRF firmware, which provides a means to program the SPI flash. The SPI flash will be programmed with the second file, called portapack-h1-firmware.bin.

To install the firmware into the HackRF's SPI flash, hold down the HackRF's DFU button (the button closest to the antenna jack) and plug the HackRF into a USB port on your computer. After the HackRF is plugged in, you may release the DFU button.

Use the DFU utility to download the hackrf_one_usb.dfu image file into the HackRF:

    dfu-util --device 1fc9:000c --download hackrf_one_usb.dfu --reset

Then, erase the HackRF SPI flash and write the PortaPack code into SPI flash:

    hackrf_spiflash -w portapack-h1-firmware.bin

Unplug your HackRF from your computer, wait a few seconds, and plug it back in. You should now be running PortaPack code.

**NOTE**: If you have an old HackRF (purchased before 2015) and have never updated your HackRF CPLD bitstream, you might also want to do that now, [as advised under "Updating the CPLD" on the HackRF Wiki](https://github.com/mossmann/hackrf/wiki/Updating-Firmware). There was a change around April 2014 that is required for PortaPack and newer gr-osmosdr host libraries. If the HackRF CPLD bitstream is old, you may encounter odd behavior -- frequencies being a few MHz off, and lots of baseband harmonic distortion.

## Restoring HackRF Firmware

Download the HackRF firmware from the [HackRF project's releases section](https://github.com/mossmann/hackrf/releases/). Extract the release archive and change directories into the archive. Then change directories into firmware-bin:

    cd firmware-bin

Plug the HackRF into USB power while holding down the DFU button (the button closer to the antenna jack). Release the DFU button. Then run:

    dfu-util --device 1fc9:000c --download hackrf_one_usb.dfu --reset

The HackRF firmware is now running from the microcontroller's RAM. Do not reset the HackRF at this point. Flash the HackRF firmware thusly:

    hackrf_spiflash -w hackrf_one_usb.bin

Once this command completes, you may either unplug the HackRF or press the RESET button, and the HackRF firmware will run from the flash memory.

## Document TODOs

*  Diagram of DFU button location