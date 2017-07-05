# `yubikey-hotplug`: Automatic screen lock/unlock for Yubikeys configured with challenge-response unlock

This is a small script that allows the running desktop environment's screensaver to be locked/unlocked based on hotplug events of a Yubikey. It has the following features:

* Fast and responsive, triggered via a udev hook
* Confined to specific Yubikey serial numbers per-user
* No root access required for configuration

## Dependencies

This utility depends on `yubikey-manager` which is available in the Arch Linux `community` repository.

## Setup

To configure `yubikey-hotplug`, all you need to do is write your Yubikey's serial number to a file in your home directory:

```
mkdir -p ~/.config/yubikey-hotplug
echo `ykinfo -s -q` > ~/.config/yubikey-hotplug/serials
```

If you don't know your Yubikey's serial number, use `ykinfo -s -q` to get it. If `ykinfo` can't figure out what it is then this program will not work, as it uses `ykinfo` to query the Yubikey's serial number. Note that some very old Yubikeys do not have serial numbers.

## Security

Unlike other attributes, the serial number is completely burned into the Yubikey and no two will ever be the same. It is theoretically possible to make a fake device with the same hwid and API as a Yubikey. There is no challenge-response or other secret key based authentication that occurs when the system verifies the Yubikey's serial number. So keep this in mind, this utility is a convenience aid and not a replacement for proper workstation security.
The Yubikey has to be taken out of the computer for this system to properly lock the computer. If this one is autolocked, a simple push on the Yubikey button will unlock it again, so __TAKE OUT YOUR YUBIKEY WHEN YOU LEAVE YOUR COMPUTER__.

## Limitations

Right now, pretty much nothing. Adding a challenge/response system to authenticate the Yubikey better than with its serial number will be investigated.

## Author/License

Written by Dan Fuhry <dan@fuhry.com>.

Modified by Romain Bazile.

MIT licensed; please see the [COPYING file](COPYING).
