## LCD

The LCD is a LED-backlit TFT with 2.4" (61mm) of display area. The [ILI9341 controller](http://www.newhavendisplay.com/app_notes/ILI9341.pdf) is built in to the LCD, and the LCD modules are configured for the 8080-I MCU 16-bit bus interface (IM[3:0] = 0001). The 8-bit interface from the HackRF is converted to 16 bits via the PortaPack's CPLD. The CS (chip select) pin is permanently grounded. The LED backlight is controlled by a MOSFET on the PortaPack board, which is controlled by a register bit in the PortaPack CPLD.

The "Tearing Effect" pin provides a positive pulse whenever the display refresh reaches a particular scan line (default "0"). This signal is used to synchronize display code on the PortaPack. During testing of the first batch of PortaPacks, it was observed that the refresh rate of the LCDs varied by a wide margin (73 to 79Hz). It appears that the LCD "fosc" is determined by an RC oscillator or similar, and is quite temperature-dependent. The frame rate slows as the device warms up.