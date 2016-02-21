An analog audio receiver is available via the "Receiver->Audio" menu path. Common AM and FM modes are implemented.

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