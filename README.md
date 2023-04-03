# Hackintosh - MEDION Akoya E6418 aka CX 22953
Creating a Hackintosh into MEDION Akoya E6418 MD99620 (aka CX 22953)

### Working
- Intel Core i5-5200U CPU @ 2.20GH
- Intel HD Graphic 5500: Broadwell
- Broadcom 802.11ac Network Adapter: BCM94352HMB
- Realtek High Definition Audio: ALC269 VC (alcid=35)
- Realtek PCIe GBE Family Controller Realtek: RTL8168
- CMN15BE 1366 x 768 @ 60 Hz 15.3 inches
- Realtek Semiconductor Corp. 57da Built-In Video Camera
- Trackpad ELAN etd042F
- Keyboard
- Brightness
- Battery status: D15 
- Sensors:  Proccesors & Devices
- USB: 2x3.0 & 2x2.0

### Not tested
- HDMI
- SD Card Reader

### Not Working
- NVIDIA GeForce 940M (Maxwell): [Not supported](https://dortania.github.io/GPU-Buyers-Guide/modern-gpus/nvidia-gpu.html#native-nvidia-gpus)
- RTL8723BE Realtek 802.11b/g/n: [Replaced](https://dortania.github.io/Wireless-Buyers-Guide/unsupported.html#supported-chipsets)

---

## Extra devices needed for installation
* MacOS or Hackintosh PC: for creating installer
* USB 2.0 Flash Drive 16 GB: for USB installer
* [USB Wifi Stick MacOS compatible](https://dortania.github.io/Wireless-Buyers-Guide/types-of-wireless-card/usb.html): until Broadcom Wifi could be installed
* USB Keyboard MacOS compatible: until PS2 Keyboard is installed
* USB Mouse MacOS compatible: until PS2 Trackpad is installed
* [Wifi card MacOS compatible](https://dortania.github.io/Wireless-Buyers-Guide/unsupported.html#supported-chipsets)

---

## BIOS Settings
1. Using Windows, update your BIOS with [official Medion BIOS updater](http://www1.medion.de/downloads/index.pl?op=detail&id=15384&type=treiber&lang=uk)
2. Into the BIOS (turn on the computer and press F2) change settings to:
* Intel Virtualization Technology : Enable
* Legacy USB Suppor: Enable
* USB Charger: Enable
* TPM Device: Enable
* Secure Boot: Disabled
* Secure Boot Mode: Standard
* Fast Boot: Disabled
* CSM Support: Enabled
* PXE Boot: Disabled
* SATA Mode Selection: AHCI
3. Press F10: Save & Exit

---

## Install

[Mojave - Clover](mojave.md)<br>
[Big Sur - OpenCore](bigsur.md)

---

## Modifier keys for Windows Keyboard
1. Go to Keyboard > Modifier Keys...
2. Set
* Caps Lock: Caps Lock
* Control: Command
* Option: Option
* Command: Control

---

## Alt-tab for Windows Keyboard
1. Download and Install [Alt-Tab](https://alt-tab-macos.netlify.app)

---

## Sensors
1. Download and install [Intel Powe Gadget](https://software.intel.com/content/www/us/en/develop/articles/intel-power-gadget.html)
2. Download and install [HWMonitorSMC2](https://github.com/CloverHackyColor/HWMonitorSMC2/releases) and activate options inside.
3. Downlaod and install [HWSensors](https://sourceforge.net/projects/hwsensors/) but deactivating FakeSMC and all FakeSMC options.
4. Reboot

---

## Thanks
* [Diskmaker X](https://diskmakerx.com/download/)
* [TonyMac](https://www.tonymacx86.com/resources/categories/tonymacx86-downloads.3/)
* [Dortania](https://dortania.github.io/)
* [Rehabman](https://github.com/RehabMan)
* [Mieze](https://github.com/Mieze/RTL8111_driver_for_OS_X)
* [Noobsplanet](https://noobsplanet.com)
* [Adidanthera](https://github.com/acidanthera)
* [AIOBoot](https://www.aioboot.com)
* [Neosergio](https://github.com/neosergio)
* [SIL Ls Dev](https://github.com/sillsdev)
* [Lwouis](https://github.com/lwouis)
* [IMHO Production](https://www.youtube.com/watch?v=jvuIpX2MUCk)
* [Femi Ojeyemi](https://youtu.be/ZC0NHWc8ibE)
* [Idea Visual Tech](https://youtu.be/iPX3oiBJZZc)
* [RidhaF](https://github.com/RidhaAF/Hackintosh-Asus-A455LB)

