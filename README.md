# android_device_lenovo_zippo
For building TWRP for Lenovo Z5 Pro GT

TWRP device tree for Lenovo Z5 Pro GT

## Features

Works:

- ADB
- Decryption of /data
- Screen brightness settings
- Correct screenshot color
- MTP
- Flashing (opengapps, roms, images and so on)
- Backup/Restore (Needs more testing)
- USB OTG

TO-DO:

- Vibration support

## Compile

First checkout minimal twrp with omnirom tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
repo sync
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/lenovo/heart" name="HighwayStar/android_device_lenovo_heart-twrp" remote="github" revision="android-9.0" />
```

You need also of this commit in /build:

```
https://gerrit.omnirom.org/#/c/android_build/+/36483/
```


Finally execute these:

```
. build/envsetup.sh
lunch omni_heart-eng
mka recoveryimage ALLOW_MISSING_DEPENDENCIES=true # Only if you use minimal twrp tree.
```

To test it:

```
fastboot boot out/target/product/heart/recovery.img
```

## Other Sources

Kernel source: https://github.com/Lucchetto/android_kernel_lenovo_sm8150

## Thanks

Thanks to @Lucchetto for the kernel
