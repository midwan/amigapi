# amigapi
A script to configure a stock [MINIBIAN] system as a dedicated Amiga emulation machine.

Usage
-----

~~~ bash
wget --content-disposition https://git.io/v6qwy
sh ./amigapi

What next?
----------
The tool will present you with a menu containing all available options.
You should start with expanding the filesystem, Upgrading the system and finally install AmigaPi.
The rest of the options are there for making things easier for novice users.

Troubleshooting WiFi
--------------------
If your `wlan0` is not working after rebooting, you're probably missing kernel
firmware for your wireless network adapter.

Just check `dmesg` for entries looking like:

> r8188eu 1-1.5:1.0: **Firmware** _rtlwifi/rtl8188eufw.bin_ **not available**


and use `apt-file` to find the corresponding package containing this firmware:

~~~~ bash
apt-file update
apt-file find rtl8188eufw.bin
~~~~


which will result in:

~~~~ shell
firmware-realtek: /lib/firmware/rtlwifi/rtl8188eufw.bin
~~~~


and then install the required package:

~~~~ bash
apt-get -y install firmware-realtek
~~~~


Now unplug and reinsert the wireless adapter or reboot.


[MINIBIAN]: https://minibianpi.wordpress.com/
