The PortaPack has its own firmware. Here's how to build it from scratch:

## Tools

* [GCC-ARM-Embedded](https://launchpad.net/gcc-arm-embedded) - I am using the "4.9-2015-q2" release.
* [dfu-util](http://dfu-util.sourceforge.net) - Use the 0.7 release. Newer releases remove the necessary "-s" option.

## Building

Once you have a built binary, you need to [Update the Firmware](Updating-Firmware) on the HackRF One.