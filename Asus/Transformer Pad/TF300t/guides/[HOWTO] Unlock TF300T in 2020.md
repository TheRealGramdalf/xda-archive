# UPDATE: Asus has updated the servers. Older protocols for HTTPS, which are required for older Android versions, are no longer supported. Unfortunately, some additional steps are needed for the unlock now. See [this post](https://forum.xda-developers.com/t/howto-unlock-tf700t-in-2020.4157143/page-8#post-85097463) for step by step instructions.


I recently got my hands on a Asus TF700T with a locked boot loader. The official unlock app did not work, so I took a closer look. What I found is that the Asus servers are still up and running, but connection fails due to certificate pinning. And that can be dealt with ;)

So here are the instructions:

    The device must be rooted. KingoRoot (the app) worked for me.

    Download the unlock bundle from the link below.

    Copy both apks to /system/app, change the permission to 0644
    For this, a remount of the system partition may be needed; you can use `adb shell` to enter a remote shell, and `su` to gain root privileges.
     `mount -o remount,rw -t ext4 /dev/block/mmcblk0p1 /system`

    DMClient.apk replaces the original DMClient.apk and DMClient.odex (i.e. you have to rename/move/delete the .odex file)
    The modified unlock app cannot be installed like any other and must be installed that way

    Reboot the device. On startup Android shows that one app is optimized (that's DMClient). The unlock app is now installed.

    Use the unlock app. Google account does not matter.


Watch logcat to get some more information on what the unlock app does. On success the device immediately reboots, so redirect adb logcat to a file if you want to keep the log.

I only tested on a TF700T with WW SKU, V10.6.1.14.10. I assume that other firmware versions work as well.
The unlock app for TF700T also supports TF201, TF300T, TF300TG, and TF300TL, but a modified DMClient is needed.


In case something goes wrong and your device gets stuck at the boot screen, this advice may be helpful:
https://android.stackexchange.com/questions/28077/bricked-my-asus-tf300t-manual-jb-update
(thanks @DieAbrissbirne)


Download links

[Unlock app and DMClient for TF300T](https://github.com/TheRealGramdalf/xda-archive/tree/main/Asus/Transformer%20Pad/TF700T/resources)
