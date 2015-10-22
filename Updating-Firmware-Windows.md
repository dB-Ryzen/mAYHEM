If you're using Windows, use the PortaPack Firmware Tool to put PortaPack firmware into your HackRF One. Here's the procedure:

Download and run this installer: [PortaPack Firmware Tool](http://www.sharebrained.com/downloads/portapack/windows/PortaPack%20Firmware%20Tool-1.0.0.exe) (1.0.0, 64-bit only, 3.16Mbytes)

Windows SmartScreen may warn you about running this program. If so, tell Windows to run the program anyway.

You will be asked if you want to allow the program to make changes to your computer. Answer "Yes".

![Windows UAC warning for ShareBrained Technology](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/windows/uac_installer_sharebrained_win81.png)

You will be asked to accept the GNU General Public License Version 2. Click "I Agree".

![Accept the GNU GPLv2 license](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/windows/gpl_v2_accept_win81.png)

You will be asked twice to install device software from ShareBrained Technology. The first is for the HackRF driver, and the second is for the NXP LPC DFU mode driver. Click "Install" both times. Or if you're feeling especially bold, you can check "Always trust software from ShareBrained Technology, Inc.", and Windows will never ask again if you trust ShareBrained Technology.

![Install device software from ShareBrained Technology](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/windows/install_device_firmware_sharebrained_win81.png)

The installer will finish. Click "Close".

![Installer finished](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/windows/installer_finished_win81.png)

You will now have a "PortaPack" program group with two shortcuts. One will flash the PortaPack firmware onto your HackRF. The other will flash the stock HackRF firmware (with no PortaPack functions).

![PortaPack program group](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/windows/program_group_win81.png)

To install PortaPack firmware on your HackRF, click on the "Flash PortaPack Firmware" shortcut. A DOS prompt will appear on screen. Just follow the instructions!

![PortaPack firmware installation](https://raw.github.com/sharebrained/portapack-hackrf/master/doc/images/wiki/windows/portapack_firmware_install_cmd_win81.png)

I don't claim to be a Windows developer, so I'm sure it won't work perfectly for everybody. So if you have any problems or questions, please <a href="mailto:support@sharebrained.com">e-mail me</a>!