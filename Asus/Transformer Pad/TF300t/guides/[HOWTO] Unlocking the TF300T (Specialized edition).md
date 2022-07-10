

This guide is based off the original guide from XDA user [d.l.i.w](https://forum.xda-developers.com/m/d-l-i-w.11054847/)

Download the unlock_V7.apk and DMClient.apk from the download link below, as well as the KingoRoot app (if the KingoRoot.apk doesn't work, try the windows edition, or any other root app.)

Copy all the files to your tablet and install the KingoRoot app (or your chosen root app-- but that app only!) on your tablet. If you have the dock, a regular USB stick with fat32 file system should work. If not, you can use a micro SD card, or use ADB to sideload (install) the app. USB debugging will need to be enabled (see original guide)
    `adb sideload "Kingo ROOT_v3.3.apk"`
Once kingoroot is installed, run the root process.
After that is completed, you will need either a terminal on your device, or ADB shell. 
    Terminal emulator app
or
    `adb shell`
Once you are in the shell, you can begin the rest of the process. First, gain root access. Do this by entering `su` in the command line. Your tablet may prompt you to allow root access.
Now you have root access. Locate the directory you put the DMClient and unlock app *.apk in by using `cd` and `ls`. To find the path of the file, locate it within the files app on your tablet, and the path should be displayed up top. It should look something like this: `/sdcard/Download/`. Then you can `cd /sdcard/download` and use `ls` to verify you are in the correct location.
Now, go ahead and remount your `/system` partition to gain read/write privileges. Enter the following command into the terminal (adb shell or terminal emulator) `mount -o remount,rw -t ext4 /dev/block/mmcblk0p1 /system`. If you get an error saying that the resource/partition is busy, reboot your tablet and reenter the shell. 

Now, try copying the files to the `/system/app/` directory. If you rebooted, you will need to `cd` to the correct location again, as well as `su` to gain root access.
Move the original DMClient.apk and DMClient.odex into a backup
    `mv /system/app/DMClient.apk /system/app/DMClient.apk.bak`
    `mv /system/app/DMClient.odex /system/app/DMClient.odex.bak`
Try copying the modified files with the following commands:
    `mv UnLock_App_V7_update.apk /system/app/`
    `mv DMClient.apk /system/app/`
If that throws the 'failed on 'UnLock_App_V7_update.apk' - Cross-device link' error, then do the following:
    `touch /system/app/unlock.apk` - creates an empty file in /system/app
    `touch /system/app/DMClient.apk` - same thing

    `cat Unlock_App_V7_update.apk > /system/app/unlock.apk` - Outputs the contents of the modified unlock app and essentially copy them to the /system/app/unlock.apk file
    `cat DMClient.apk > /system/app/DMClient.apk` - same thing but for dmclient

Now for safe measure, reboot your tablet. The unlock app should be in the application menu (it's hard to find, it blends in well).

Then proceed with the guide on setting up mitproxy and go through the unlock process. Hopefully you have an unlocked bootloader!
    

Downloads:

[Unlock app and DMClient for TF300T](https://github.com/TheRealGramdalf/xda-archive/tree/main/Asus/Transformer%20Pad/TF700T/resources)
[KingoRoot (Android)](https://github.com/TheRealGramdalf/xda-archive/blob/main/Asus/Transformer%20Pad/TF300t/resources/Kingo%20ROOT_v3.3.apk)
[KingoRoot (Windows)](https://github.com/TheRealGramdalf/xda-archive/blob/main/Asus/Transformer%20Pad/TF300t/resources/KingoRoot_TF300T.exe)