# Customized smarthphone with Lineage OS on a Samsung Galaxy A5 (2016)

```
AUTHOR: Samuel M.H.
DATE: 18-AUG-2021
LICENCE: all rights reserved.
```

## Introduction

Time ago a got an old Samsung Galaxy A5 (SM-A510F) and I wanted to update it with the latest available Android version and some applications that made me feel I am the "owner" of the phone. If you come from the linux world, you know what I mean. By the way, it is a guide for linux users.

This is a guide on how I configured the phone as well as a lot of resources to solve most of the problems you will encounter.

### Considerations
The Android distribution I chose was [LineageOS](https://lineageos.org/). "_A free and open-source operating system for various devices, based on the Android mobile platform._"

1. Check the device is supported: [Info about a5xelte](https://wiki.lineageos.org/devices/a5xelte).
2. The guide I followed: [Install LineageOS on a5xelte](https://wiki.lineageos.org/devices/a5xelte/install).


## Bootloader / Recovery Mode - TWRP
The first thing is to install a bootloader. TeamWin Recovery Project is like a secondary OS that resides on a different partition and provides a recovery mode with advanced functions: flash a new OS ROM, add packages to OS level, encryption, ... Something like a bootloader like GRUB.

* Documentation for the phone: [TWRP for Samsung Galaxy A5 2016 (Exynos)](https://twrp.me/samsung/samsunggalaxya52016exynos.html)

<i>NOTE:
If you are using **Windows**, use the official Samsung flashing software Odin.
* [Samsung Odin - Official Odin Download links](https://samsungodin.com)
* [Download Odin](https://odindownload.com).
</i>

To be clear, we are in [this](https://wiki.lineageos.org/devices/a5xelte/install#preparing-for-installation) part of the guide.
For **Linux** users:

1. Download the TWRP .img from the web.
2. Get [Heimdall](https://github.com/Benjamin-Dobell/Heimdall). I found it on the official Ubuntu repository `apt-get install heimdall-flash` (Version 1.4.2).
3. Start your phone into download mode `[Volume Down] + [Home] + [Power]` and plug it with the usb cable to the computer.
4. Flash the device.
```bash
sudo heimdall flash --RECOVERY twrp-3.5.2_9-0-a5xelte.img --no-reboot
```
5. Wait and restart the device with `[Volume Down] + [Power buttons]` for 8~10 seconds.
6. Start the device with `[Volume Up] + [Home] + [Power]` to boot into TWRP. Congratulations!

_NOTE: One way to test if Heimdall is working is to connect the smartphone and launch. Is everything works, the device will restart. _
```bash
sudo heimdall print-pit
```

_NOTE: It did not work at the first time, so probably you will have to repeat the steps until it works._



## System and utilities
Now we are going to install the OS as well as some useful packages. The trick is to use the ADB Sideload option to upload `.zip` files to the phone.

1. In your computer you should have installed `adb`. In my case `apt-get install adb` (Version 1:8.1.0+r23-5ubuntu2)
2. Boot the phone in revovery mode with `[Volume Up] + [Home] + [Power]`.
3. Go to Advanced > ADB Sideload > Swipe to Start Sideload. Documentation:[TWRP ADB Sideload](https://twrp.me/faq/ADBSideload.html)

The phone will be waiting for the computer to receive the files.


### Lineage OS ROM

The first thing is to install the Android ROM we have chosen. We are in [this](https://wiki.lineageos.org/devices/a5xelte/install#installing-lineageos-from-recovery) part of the guide.

1. [Download](https://download.lineageos.org/a5xelte) the latest LineageOS ROM.
2. Send it to the phone. _You should change the name of the .zip file in the command._
```bash
adb sideload lineage-17.1-20210627-nightly-a5xelte-signed.zip 
```

_NOTE: Upload stops at 47% and is OK.__


### Google Apps (optional)

If you want to use Google Apps, you have to upload the package right now.

* The [reason](https://wiki.lineageos.org/gapps.html)
* [Where](https://opengapps.org/?api=10.0&variant=stock&arch=arm) I got the package (the pico version). 
* Send it to the phone. Maybe you have to get into the (ADB Sideload again)
```bash
adb sideload open_gapps-arm-10.0-pico-20210619.zip
```


### Magisk (optional)

[Magisk](https://github.com/topjohnwu/Magisk) is a suite of open source software for customizing Android. It is interesting because it runs at a root level, instead of of a user level and has access to the OS functions. This allows apps to:
* Record calls.
* Control how the battery is charged, probably incrementing its lifespan.
* Equalize the sound of the phone.

Furthermore, it will pass the [SafetyNet](https://developer.android.com/training/safetynet/attestation) checks that require not to have a rooted device and are mandatory to use some Apps (online banking).

This is the [official guide](https://topjohnwu.github.io/Magisk/install.html). The method I present seems to be deprecated, but in my case worked fine. 

Steps:
1. [Download the apk](https://github.com/topjohnwu/Magisk/releases) and rename it to a `.zip` extension.
2. Inside TWRP: Advanced > ADB Sideload > Swipe to Start Sideload
6. On the PC.
```
adb sideload Magisk-v23.0.zip
```

### Reboot the system
Reboot the system!

```bash
adb sideload Magisk-v23.0.zip
```

If everything goes right, you will have the base of your new customized mobile.

Congratulations!
