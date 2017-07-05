# WORK IN PROGRESS, READ CAREFULLY THE SCRIPTS, IF YOU DON'T UNDERSTAND, DON'T USE!


# `yubikey-hotplug`: Automatic screen lock/unlock for Yubikeys

This is a small script that allows the running desktop environment's screensaver to be locked/unlocked based on hotplug events of a Yubikey. It has the following features:

* Fast and responsive, triggered via a udev hook
* Confined to specific Yubikey serial numbers per-user
_* No root access required for configuration_
_* Secure - workstation cannot be unlocked with a yubikey if it was unplugged while the PC was locked_

## Dependencies

This utility depends on `yubikey-manager` which is available in the Arch Linux `community` repository.

## Setup

To configure `yubikey-hotplug`, all you need to do is write your Yubikey's serial number to a file in your home directory:

```
sudo mkdir -p /root/.config/yubikey-hotplug
sudo echo `ykinfo -s -q` > /root/.config/yubikey-hotplug/serials
```

If you don't know your Yubikey's serial number, use `ykinfo -s -q` to get it. If `ykinfo` can't figure out what it is then this program will not work, as it uses `ykinfo` to query the Yubikey's serial number. Note that some very old Yubikeys do not have serial numbers.

## Security

Unlike other attributes, the serial number is completely burned into the Yubikey and no two will ever be the same. It is theoretically possible to make a fake device with the same hwid and API as a Yubikey. There is no challenge-response or other secret key based authentication that occurs when the system verifies the Yubikey's serial number. So keep this in mind, this utility is a convenience aid and not a replacement for proper workstation security.

## Limitations

The utility currently works only with my username, still need to add support for automatic detection of users (unless the .config is pushed in the `root` user home directory...

## Author/License

Written by Dan Fuhry <dan@fuhry.com>.

Modifier by Romain Bazile.

MIT licensed; please see the [COPYING file](COPYING).
