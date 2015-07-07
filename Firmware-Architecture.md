# Firmware Architecture

The HackRF One's LPC4320 dual-core microcontroller has limited resources for doing software-defined radio work. There's a total of 200Kbytes of RAM and 1Mbyte of SPI flash memory.

## Memory Map

Absolute addresses on the HackRF One LPC4320:

    0x0000_0000 0x1000_0000     Shadow area (controlled by CREG M4MEMMAP and M0APPMEMMAP)
    0x1000_0000 0x1001_8000 96k Local SRAM
    0x1008_0000 0x1008_8000 32k Local SRAM
    0x1008_8000 0x1008_a000  8k Local SRAM (VBAT domain)
    0x1400_0000 0x1410_0000  1M SPIFI flash (cached access to W25Q80BV flash IC)
    0x2000_0000 0x2000_8000 32k AHB SRAM
    0x2000_8000 0x2000_c000  8k AHB SRAM
    0x2000_c000 0x2001_0000  8k AHB SRAM (also ETB)
    0x2200_0000 0x2400_0000 32M AHB SRAM bit-banding (only from M4 core?)
    0x4000_0000 0x4010_2000     Peripherals
    0x4200_0000 0x4400_0000 32M Peripherals bit-banding (only from M4 core?)
    0x8000_0000 0x8010_0000  1M SPIFI flash (direct access to W25Q80BV flash IC)
    0xe000_0000 0xe010_0000     ARM core private bus (distinct for M4 and M0 cores)

How RAM and flash regions are used in PortaPack code:

    0x1000_0000 0x1001_8000 96k Local SRAM for M4 RAM (stack, heap, data)
    0x1008_0000 0x1008_8000 32k Local SRAM for M4 code (text section)
    0x1008_8000 0x1008_a000  8k Local SRAM for M4/M0 communication, persistent state
    0x1400_0000 0x1410_0000  1M SPIFI flash for M4 bootstrap, M0 code, M4 code overlays
    0x2000_0000 0x2001_0000 64k AHB SRAM for M0 RAM (stack, heap, data)

#### Philosophy

M4 code is run from local SRAM for performance reasons. The smaller local SRAM region is used because DSP code tends to be tight loops and doesn't require much code.

M4 data is kept in a separate local RAM block to maximize performance. The M4 core can retrieve instructions and data from separate blocks simultaneously through use of distinct I-code and D-code buses. The larger local SRAM region is used to maximize storage for baseband data, filter coefficients, and intermediate data.

M0 code is run from flash (mostly) because the UI and non-critical code is much larger than the DSP code on the M4. So the performance hit is outweighed by the extra code storage. The SPIFI interface is cranked up to maximum performance -- 100MHz SCK, quad SPI interface, minimum CS# idle time, fastest SCU mux pins mode, read through cached memory region. Without addressing overhead, this provides 400Mbps transfer, or 50Mbytes/s or 12.5Mwords/sec. Overhead for flash bursts (0xEB instruction) is ~20(!) clocks or 200ns(!!). It's unclear how large a region SPIFI caches, but it's probably on the order of 16/64/256 bytes.

M0 data is in the AHB RAM region, to avoid contention with the M4 core's code and data.

The VBAT domain local SRAM block is used for communication between cores. It's also used to save data to re-initialize the device at power-up and return the user to the state before power-off. M0 code should avoid reading from this region any more than necessary, to avoid slowing down the M4 core.

M4 and M0 data RAM is accessed via direct addressing. This permits passing pointers between the M4 and M0. Of course, passing pointers to the M4 or M0 text sections (RAM shadowed/aliased to 0x0) wouldn't work without some sort of address fix-up to point into M4 RAM or the M0 SPIFI image.

## TODOs

* Hook up scope and determine SPIFI caching behavior. There may be locality-of-reference or function alignment tricks to improve performance -- when it's needed.
* Investigate using SPI flash 0xEB instruction with M[5:4] = 0b10, to eliminate eight cycles of overhead.
* If SPIFI cache always aligns amenably, perhaps use a different SPI flash instruction that assumes some address LSBs are zero (aligned) to eliminate a cycle or two of overhead.
* If SPIFI transfers always have A[0] == 0, use 0xE7 instruction to eliminate two clocks of overhead over 0xEB.
* If SPIFI transfers always have A[3:0] == 0, use 0xE3 instruction to eliminate four clocks of overhead over 0xEB.