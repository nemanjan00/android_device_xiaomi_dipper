# android_device_xiaomi_dipper
For building TWRP for Xiaomi Mi 8, with block based encryption

TWRP device tree for Xiaomi MI 8

## Features

Works:

- Block based encryption
- ADB
- Decryption of /data
- Screen brightness settings
- Vibration on touch 
- Correct screenshot color 

## Changing encryption

Replace `/vendor/fstab.qcom` with version from this repo.

## Compile

First checkout minimal twrp with omnirom tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
repo sync
```

Then add these projects to .repo/manifest.xml:

```xml
<project path="device/xiaomi/dipper" name="nemanjan00/android_device_xiaomi_dipper" remote="github" revision="android-9.0" />
```

Finally execute these:

```
. build/envsetup.sh
lunch omni_dipper-eng
mka recoveryimage ALLOW_MISSING_DEPENDENCIES=true # Only if you use minimal twrp tree.
```

To test it:

```
fastboot boot out/target/product/dipper/recovery.img
```
## Contributors

[Here](https://github.com/TeamWin/android_device_xiaomi_dipper/graphs/contributors)

## Other Sources

Kernel Sources: https://github.com/LineageOS/android_kernel_xiaomi_sdm845

## Thanks

- Thanks to @notsyncing for the base: https://github.com/notsyncing/android_device_xiaomi_polaris
