# android_device_lenovo_zippo
For building TWRP for Lenovo Z6 Pro

TWRP device tree for Lenovo Z6 Pro

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
<project path="device/lenovo/zippo" name="mauronofrio/android_device_lenovo_zippo" remote="github" revision="android-9.0" />
```

Finally execute these:

```
. build/envsetup.sh
lunch omni_zippo-eng
mka recoveryimage ALLOW_MISSING_DEPENDENCIES=true # Only if you use minimal twrp tree.
```

To test it:

```
fastboot boot out/target/product/zippo/recovery.img
```

## Other Sources

Kernel source: https://github.com/Lucchetto/android_kernel_lenovo_sm8150

## Thanks

Thanks to @Lucchetto for the kernel
