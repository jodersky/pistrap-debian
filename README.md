# pistrap-debian

Create a bootable Debian SD card for the RaspberryPi 2.

Pistrap-debian is a shell script that partitions and mounts an SD card and subsequently creates a bootable root file system for the RaspberryPi 2.

The root filesystem is that of a minimal Debian Jessie distribution with the kernel pulled in from the Raspbian archive. Furthermore, hostnames, timezones, passwords, networking and SSH are setup as to remove the need of any additional screen-and-keyboard configuration.

## Requirements
Debian-based host system with the following packages:

- qemu-user-static
- parted

The resulting image is only compatible with ARMv7 processors (armhf Debian distribution), hence the requirement of a RaspberryPi 2.

## Usage
```
Usage: pistrap-debian [OPTION]... DEVICE

Create a bootable image for a RaspberryPi 2 on DEVICE.

Options:
  --force                           Don't ask for any confirmations.
  --mirror=<$MIRROR>                Use a debian mirror, such as "fr" or "ch"
  --hostname=<$HOSTNAME>            Use a given hostname for the device.
  --timezone=<$TIMEZONE>            Set timezone data as listed in /usr/share/zoneinfo
  --wpa-essid=<$WPA_ESSID>          Use a given wireless ESSID. Sets up wireless networking.
  --wpa-psk=<$WPA_PSK>              Use a given WPA pre-shared key.
  --password=<$ROOT_PASWORD>        Set the given root password.
  --ssh-key=<$SSH_KEY>              Add the given SSH key to root's authorized_keys file. If invalid, password login will be enabled.
  --root-fs=<$ROOTFS>               Use given directory as mount point during installation.
```

## Caveats
- The script is very fragile. Should anything unexpected happen during the installation process, the script will abort and manual unmounting will be required.
Also, the script must be run on an unmounted SD card and, in case of interruption, cannot resume.

## Origin
The commands run by the script are adapted from two documents on creating bootable file systems:

- USB Armory, https://github.com/inversepath/usbarmory/wiki/Preparing-a-bootable-microSD-image, by Andrea Barisani and others

- Stock Debian Jessie on the Raspberry Pi 2, https://0xstubs.org/stock-debian-jessie-on-the-raspberry-pi-2/, by Michael Laß

## Copying
Copyright (c) 2015 Jakob Odersky

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License version 2 as published by the Free Software Foundation.
