### Power Sources

The PortaPack is powered via the USB 2.0 connector on the HackRF One. You can power the system over the USB connector in a number of ways. Here are a few ideas:

* USB 2.0 cable to a host computer.
* USB 2.0 cable to a rechargeable battery with a USB interface. Most any commercially available USB-connected battery should work, though they vary greatly in quality.
* A 5V, >500mA DC power supply with a USB type A jack, and a standard micro USB cable. For instance, the [Adafruit 5V 1A power supply with USB-A connector](https://www.adafruit.com/products/501) or the [Adafruit 5V 2A power supply with USB-A connector](https://www.adafruit.com/products/1994).
* A 5V, >500mA DC power supply with a cable that terminates in a micro USB connector. For instance, the [Adafruit 5V 2A switching power supply with 20AWG 6' micro USB cable](https://www.adafruit.com/products/1995).
* A USB 2.0 adapter to a 5V, >500mA DC power supply. For instance, the [Adafruit 5V 2A switching power supply](https://www.adafruit.com/products/276) with the [Adafruit micro USB plug to 5.5/2.1mm DC barrel jack adapter](https://www.adafruit.com/products/2727) or the [Adafruit micro USB to 5.5/2.1mm DC barrel jack adapter](https://www.adafruit.com/products/2789).

Depending on the design of power source and the quality and length of your USB cable, noise from the power source can be induced into the radio and cause spurious noise to be received or transmitted. The performance of the antenna system (especially telescoping monopoles like the ANT500) can be affected by the cable and power source.

Switching power supplies are theoretically less desirable than linear power supplies, as they can induce switching noise into the radio, but linear power supplies are less power efficient.

### Power Consumption

The PortaPack is limited by the power available through the USB 2.0 connector -- typically 2.5 Watts (5V @ 500mA). Power consumption will vary depending on what activities the PortaPack is performing. Here are some informal measurements taken in February 2016 using the latest firmware:

| PortaPack Activities | Typical Power Consumption |
| -------------------- | ------------------------- |
| Idle at top menu | 1.2 W |
| Receive AM or SSB audio | 1.9 W |
| Receive narrowband FM audio | 1.9 W |
| Receive wideband (broadcast) FM audio | 2.0 W |
| ~16 MHz wide spectrum waterfall | 2.0 W |
| Receive AIS (boats) | 1.9 W |
| Receive ERT (utility meters) | 1.9 W |
| Receive TPMS (automobiles) | 2.0 W |

The display sleep mode reduces power consumption by approximately 300 mW.
