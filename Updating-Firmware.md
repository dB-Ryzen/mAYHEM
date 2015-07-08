The PortaPack has its own firmware, which needs to be flashed into the HackRF One SPI flash.

# Flashing

To install the firmware into the HackRF's SPI flash, run the DFU utility with the HackRF firmware built for RAM execution. Plug the HackRF into USB power while holding down the DFU button. Then run:

    dfu-util --device 1fc9:000c --download hackrf_one_usb_ram.dfu --reset

Then, erase the flash and write the Cortex-M4 and -M0 code into the SPI flash at the proper locations:

    hackrf_spiflash -w portapack_hackrf.bin
    hackrf_spiflash -d -a 131072 -w portapack_hackrf_m0.bin

Unplug your HackRF for a few seconds and plug it back in. You should now be running PortaPack code.

# Restoring HackRF Firmware

To replace the firmware on the HackRF's SPI flash with the stock HackRF firmware, plug the HackRF into USB power while holding down the DFU button. Then run:

    dfu-util --device 1fc9:000c --download hackrf_one_usb_ram.dfu --reset

The HackRF firmware is now running from the microcontroller's RAM. Do not reset the HackRF at this point. Flash the HackRF firmware thusly:

    hackrf_spiflash -w hackrf_one_usb_rom_to_ram.bin

Once this command completes, you may either unplug the HackRF or press the RESET button, and the HackRF firmware will run from the flash memory.