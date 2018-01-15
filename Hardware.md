## Audio Input/Output

The single 1/8" (3.5mm) audio jack contains both a stereo headphone output and a microphone input with DC bias. The jack is compatible with newer smart phone headsets following [the CTIA/AHJ standard](https://en.wikipedia.org/wiki/TRRS_connector#TRRS_standards). Older PortaPacks (before version 20170522) will drive 50mW into 16 Ohms. Newer PortaPacks (as of version 20170522) will drive 20mW into 16 Ohms. Both are uncomfortably loud at full volume -- just sayin'...

## LCD

The LCD is a LED-backlit TFT with 2.4" (61mm) of display area. PortaPack models before 20170522 use Kingtech DW0240A2BZ (16-bit 8080-I MCU interface, IM[3:0] = 0b0001) with resistive touch screen. PortaPack models as of 20170522 use EastRising ER-TFT024-3 with resistive touch screen (interface mode configured by PortaPack).

The [ILI9341 controller](http://www.newhavendisplay.com/app_notes/ILI9341.pdf) is built in to the LCD, and the LCD modules are configured for the 8080-I MCU 16-bit bus interface (IM[3:0] = 0001). The 8-bit interface from the HackRF is converted to 16 bits via the PortaPack's CPLD. The CS (chip select) pin is permanently grounded. The LED backlight is controlled by a MOSFET on the PortaPack board, which is controlled by a register bit in the PortaPack CPLD.

The "Tearing Effect" pin provides a positive pulse whenever the display refresh reaches a particular scan line (default "0"). This signal is used to synchronize display code on the PortaPack. During testing of the first batch of PortaPacks, it was observed that the refresh rate of the LCDs varied by a wide margin (73 to 79Hz). It appears that the LCD "fosc" is determined by an RC oscillator or similar, and is quite temperature-dependent. The frame rate slows as the device warms up.