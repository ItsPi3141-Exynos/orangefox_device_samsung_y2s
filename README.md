# OrangeFox device tree for Samsung S20+ (y2s)

## ⚙️ Kernel source

Available at <https://github.com/corsicanu/android_kernel_samsung_universal9830>

## 🛠️  How to build

### Prepare build environment

```bash
cd ~
sudo apt install git aria2 -y
git clone https://gitlab.com/OrangeFox/misc/scripts
cd scripts
sudo bash setup/android_build_env.sh
sudo bash setup/install_android_sdk.sh
```

### Clone OrangeFox

```bash
mkdir ~/OrangeFox_sync
cd ~/OrangeFox_sync
git clone https://gitlab.com/OrangeFox/sync.git
cd ~/OrangeFox_sync/sync/
./orangefox_sync.sh --branch 11.0 --path ~/fox_11.0
```

### Clone y2s device tree

```bash
cd ~/fox_11.0
git clone -b android-11 https://github.com/ItsPi3141/orangefox_device_samsung_y2s.git device/samsung/y2s
```

### Setup environment variables

```bash
. build/envsetup.sh
export ALLOW_MISSING_DEPENDENCIES=true
export FOX_BUILD_DEVICE=y2s
export LC_ALL="C"
```

### Build

```bash
. device/samsung/y2s/vendorsetup.sh
lunch twrp_y2s-eng && mka adbd recoveryimage
```

> [!NOTE]
> Sometimes, you will need to clean the build tree so that certain files can be regenerated.
>
> ```bash
> mka clean
> ```

## 🎉 Credits

### This device tree was adapted from the following repositories

- Original TWRP device tree: <https://github.com/TeamWin/android_device_samsung_y2s/tree/android-11>
- vendorsetup.sh: <https://gitlab.com/OrangeFox/device/a51nsxx>
- OrangeFox configuration: <https://gitlab.com/OrangeFox/vendor/recovery/-/blob/master/orangefox_build_vars.txt>
- Flashlight fix: <https://gitlab.com/OrangeFox/device/a72q>
- Additional reference: <https://github.com/PitchBlackRecoveryProject/android_device_samsung_z3s-pbrp/>

### Thanks to these people for their amazing work

- [Razvan (Corsicanu)](https://github.com/corsicanu)
- [Nico170420](https://github.com/Nico170420)
- [Yillié](https://gitlab.com/Yillie)
