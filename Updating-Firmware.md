The PortaPack has its own firmware, which needs to be flashed into the HackRF One SPI flash.

## Tools

You will need a few tools installed on your computer before you begin.

* [dfu-util](http://dfu-util.sourceforge.net) - Use the 0.7 release. Newer releases remove the necessary "-s" option.
* [hackrf](https://github.com/mossmann/hackrf) - All you need is the host tools, specifically, hackrf_spiflash.

## Getting the Firmware

You may download a [pre-built firmware package](http://www.sharebrained.com/downloads/portapack/firmware/portapack-firmware-20150708.zip), or [build your own firmware](Building-Firmware).

## Flashing

To install the firmware into the HackRF's SPI flash, run the DFU utility with the HackRF firmware built for RAM execution. Plug the HackRF into USB power while holding down the DFU button. Then run:

    dfu-util --device 1fc9:000c --download hackrf_one_usb_ram.dfu --reset

Then, erase the flash and write the Cortex-M4 and -M0 code into the SPI flash at the proper locations:

    hackrf_spiflash -w image.bin

Unplug your HackRF for a few seconds and plug it back in. You should now be running PortaPack code.

## Restoring HackRF Firmware

To replace the firmware on the HackRF's SPI flash with the stock HackRF firmware, plug the HackRF into USB power while holding down the DFU button. Then run:

    dfu-util --device 1fc9:000c --download hackrf_one_usb_ram.dfu --reset

The HackRF firmware is now running from the microcontroller's RAM. Do not reset the HackRF at this point. Flash the HackRF firmware thusly:

    hackrf_spiflash -w hackrf_one_usb_rom_to_ram.bin

Once this command completes, you may either unplug the HackRF or press the RESET button, and the HackRF firmware will run from the flash memory.