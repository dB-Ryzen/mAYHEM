The PortaPack has its own firmware, which needs to be flashed into the HackRF One SPI flash.

## Tools

You will need a few tools installed on your computer before you begin.

* [dfu-util](http://dfu-util.sourceforge.net) - Used to load and run the stock HackRF firmware from RAM.
* [hackrf](https://github.com/mossmann/hackrf) - All you need is the host tools, specifically, hackrf_spiflash.

## Getting the Firmware

You may download a [pre-built firmware package](https://github.com/sharebrained/portapack-hackrf/releases), or [build your own firmware](Building-Firmware).

## Flashing

If you downloaded the pre-built package, change directories to where you unzipped or untarred/unbzipped the package.

If you built your own firmware, the files you need are in the firmware/ subdirectory of your local portapack-hackrf repository.

You will need two files: hackrf_one_usb_ram.dfu, which is the stock HackRF firmware, which provides a means to program the SPI flash. The SPI flash will be programmed with the second file, called portapack-h1-firmware.bin.

To install the firmware into the HackRF's SPI flash, hold down the HackRF's DFU button (the button closest to the antenna jack) and plug the HackRF into a USB port on your computer. After the HackRF is plugged in, you may release the DFU button.

Use the DFU utility to download the hackrf_one_usb_ram.dfu image file into the HackRF:

    dfu-util --device 1fc9:000c --download hackrf_one_usb_ram.dfu --reset

Then, erase the HackRF SPI flash and write the PortaPack code into SPI flash:

    hackrf_spiflash -w portapack-h1-firmware.bin

Unplug your HackRF from your computer, wait a few seconds, and plug it back in. You should now be running PortaPack code.

## Restoring HackRF Firmware

Download the HackRF firmware from the [HackRF project's releases section](https://github.com/mossmann/hackrf/releases/). Extract the release archive and change directories into the archive. Then change directories into firmware-bin:

    cd firmware-bin

Plug the HackRF into USB power while holding down the DFU button (the button closest to the antenna jack). Release the DFU button. Then run:

    dfu-util --device 1fc9:000c --download hackrf_one_usb_ram.dfu --reset

The HackRF firmware is now running from the microcontroller's RAM. Do not reset the HackRF at this point. Flash the HackRF firmware thusly:

    hackrf_spiflash -w hackrf_one_usb_rom_to_ram.bin

Once this command completes, you may either unplug the HackRF or press the RESET button, and the HackRF firmware will run from the flash memory.

## Docuemnt TODOs

*  Diagram of DFU button location