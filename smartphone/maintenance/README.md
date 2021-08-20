# Device maintenance

```
AUTHOR: Samuel M.H.
DATE: 19-AUG-2021
LICENCE: all rights reserved.
```

Here are some tips on how to configure the device.


## The lock Screen
The first thing is to lock your device when you are not using it. It prevents other people from using it without your knowledge.

### Activate the lock screen
1. Go to `Settings > Security > Screen Lock`
2. Select a locking mechanism:
  * Pattern, drawing something on a screen grid.
  * PIN, a numeric combination.
  * Password, an alphanumeric combination.

### How and when
1. Go to `Settings > Security > Screen Lock > Gear Icon`
2. Lock after timeout. 5 seconds after screen timeout (switches off).
3. Power button instantly locks.
4. Direct unlock. The first thing to appear is the input grid.
5. Scramble layout. The order of the number in the PIN layout is altered every time.

### What to show in the lock screen
1. Go to `Settings > Display > Advanced > Lock screen display`
2. Lock Screen: Don't show notifications at all.
3. Lock screen message: maybe some email so if your mobile is lost, they can contact you.
4. Display music visualizer: On. In case you want to operate the music player without unlocking the phone.

### Camera
I find useful to use the camera without having to unlock the device.

1. Go to `Settings > System > Advanced > Gestures > Jump to camera`

### Issues
It is not possible to prevent the device to be turned off when it is locked. It is an Android design pattern in case your device get blocked and you have to restart it.

There are apps that try to offer this functionality, but if you know the button combination of the manufacturer, you will power down the device quickly.

_NOTE: In Samsung devices you force a power down by holding [Down]+[Power] for 10 seconds or so._


## Encrypt the device
Another interesting issue is what happens with you device if you lose it. You don't want your data to be exposed. An interesting approach is to encrypt the device. The stored data is unredable until your device is unblocked.

1. Go to: `Settings > Security > Encryption & credentials > Encrypt phone`
2. It is better to do this process with an empty device, so there is few data and takes more or less five minutes.



## Update the OS LineageOS
It is a good practise to update the operative system to the last version whenever possible. Usually more features are added, bugs are corrected and it is to expect the device will behave better.

1. Go to: `Settings > System > Advanced > Updater`
2. Press the refresh button. A circular arrow on the top-left corner
3. Download the last version and press "Update". The phone will reset and the new version will be installed.
4. It is possible to delete older downloaded versions since we will not use them anymore.


## Installing APKs with ADB
There are some apps that are not found in an app store and therefore distributed like a single `.apk` file.
This is a way of installing these applications.

1. Download the `.apk` file in your computer.
2. Activate "Developer mode" or "Development Settings".
  1. Go to: `Settings > About phone`
  2. Touch `Build number` (on the very bottom) repeatedly. 
3. Go to: `Settings > System > Advanced > Developer options` 
  1. Set it `On`.
  2. `Android debugging` On.
4. Connect the device to a PC.
5. Install the `.apk` file with `abd install <application>.apk`


## App stores
The usual way to install apps is through another software repository app called store, marketplace, etc.
* [Google Play Store](https://play.google.com/store/apps). It is the standard and has a dominant position, property of Google. It can be said that if you are not there you don't exist. Nearly almost all the Android devices come with the Google Play Store.
* [F-Droid](https://f-droid.org/). Another store with only free and open source apps. Very interesting if you value the FOSS world. You will have to manually install the `.apk` as shown before.

