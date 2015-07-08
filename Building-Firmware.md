The PortaPack has its own firmware. Here's how to build it from scratch:

## Tools

* [GCC-ARM-Embedded](https://launchpad.net/gcc-arm-embedded) - I am using the "4.9-2015-q2" release.
* [dfu-util](http://dfu-util.sourceforge.net) - Use the 0.7 release. Newer releases remove the necessary "-s" option.

## Getting the Source Code

The source code is hosted on GitHub. Change to a directory where you want the source code, and clone the source repository.

    git clone https://github.com/sharebrained/portapack-hackrf.git

Change directories into the cloned repository.

    cd portapack-hackrf

## Building

Change directories into the "firmware/boostrap" subdirectory.

    cd firmware/bootstrap

Make the SPI flash binary image (which builds the bootstrap, application, and baseband binaries):

    make

Once you have a built binary, you need to [Update the Firmware](Updating-Firmware) on the HackRF One.