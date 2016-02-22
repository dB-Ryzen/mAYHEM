An analog audio receiver is available via the "Receiver->Audio" menu path. Common AM and FM modes are implemented.

There are several controls common to the various modulations:

![PortaPack receiver controls](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/ui/audio/rx_controls.png)

The modulation can be set to:

* AM: amplitude modulation, including SSB and DSB).
* NFM: narrowband frequency modulation.
* WFM: wideband frequency modulation, e.g. FM broadcast.
* SPEC: spectrum analysis, approximately 15 MHz wide.

The IF and baseband gains control the gain of the second intermediate frequency IC in the HackRF.

The headphone volume adjusts from 0 to 99. Higher values can be very loud, so be careful!

The tuning frequency is in MHz, and ranges from 0.0000 MHz (0Hz, DC) to 7250.0000 MHz (7.25 GHz), with varying levels of sensitivity.

When the tuning frequency field is highlighted, pressing the "select" button on the navigation control displays the frequency entry keypad. This keypad can be operated by touch screen or with the navigation controls. The "." (period) button changes the entry position between the left and right sides of the frequency decimal point. The "<" button deletes a digit.

![PortaPack receiver frequency keypad](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/ui/audio/frequency_keypad.png)

Three colored bars display the received signal strength, baseband signal strength, and output audio level:

![PortaPack receiver levels](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/ui/audio/rx_levels.png)

All receiver views display a spectrum waterfall. Along the top is a ruler indicating the width of the view. The channel bandwidth (pass band) is depicted by green and yellow bars. The green region is the channel filter pass band, and the yellow bars are the channel filter transition regions.

![PortaPack receiver levels](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/ui/audio/waterfall.png)

### Narrowband amplitude modulation (AM):

Supported modes:

* DSB: Double side band: broadcast AM, 6kHz bandwidth
* SSB: Single side band: both upper (USB) and lower (LSB) side bands, 2.8kHz bandwidth

![PortaPack AM DSB receiver mode](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/ui/audio/am_dsb.png)
![PortaPack AM LSB receiver mode](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/ui/audio/am_lsb.png)

### Narrowband FM:

Supported modes:

* 8.5kHz bandwidth, 2.5kHz deviation
* 11kHz bandwidth, 2.5kHz deviation
* 16kHz bandwidth, 5kHz deviation

![PortaPack NFM 8.5kHz receiver mode](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/ui/audio/nfm_8k5_70cm.png)
![PortaPack NFM 11kHz receiver mode](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/ui/audio/nfm_11k_noaa.png)

### Wideband FM

One configuration of wideband FM is supported -- 75kHz deviation, 200kHz bandwidth, with 75us de-emphasis.

![PortaPack WFM receiver mode](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/ui/audio/wfm.png)

### To be implemented:

* CW receive with tunable filter
* Record to micro SD card
* Transmit functions