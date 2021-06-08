# MirkoElectronics sample code

This repository contains example code for working with the MirkoPC and BitPiRat.

Because some of the included kernel modules are GPL v2 licensed, this project as a whole has that license too. However, most code in the `hw-examples` dir is available under the MIT license.

## Fan driver

The fan driver (for the 4-pin fan) is inside the `fan-support` subdirectory.
If this is empty for you, you didn't clone this repository with the `--recursive` flag, so you still need to clone the submodule by running

```sh
git submodule init
git submodule update
```

Once you've done that, you can install the fan kernel module like this:

## Usage
1. Install dkms if you haven't already:
```
sudo apt install dkms
```
2. Open the `fan-support` directory.
```
cd fan-support
```
3. Run `./install.sh`, feel free to inspect it yourself first. It will install the current version to /usr/src with an appropriate version, and run DKMS.


## Config options
The device tree overlay has a few options, here's the equivalent of a `/boot/overlays/README` info section:

```
Name:   cm4io-fan
Info:   Raspberry Pi Compute Module 4 IO Board fan controller
Load:   dtoverlay=cm4io-fan,<param>[=<val>]
Params: minrpm              RPM target for the fan when the SoC is below 
                            mintemp (default 3500)
        maxrpm              RPM target for the fan when the SoC is above
                            maxtemp (default 5500)
        midtemp             Temperature (in millicelcius) at which the fan
                            begins to speed up (default 50000)
        midtemp_hyst        Temperature delta (in millicelcius) below mintemp
                            at which the fan will drop to minrpm (default 2000)
        maxtemp             Temperature (in millicelcius) at which the fan 
                            will be held at maxrpm (default 70000)
        maxtemp_hyst        Temperature delta (in millicelcius) below maxtemp
                            at which the fan begins to slow down (default 2000)
```

You can change these parameters in /boot/config.txt
