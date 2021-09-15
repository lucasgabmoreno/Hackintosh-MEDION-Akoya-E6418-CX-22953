# Hackintosh - MEDION Akoya E6418 aka CX 22953
This is a guide with detail of creating a laptop MEDION Akoya E6418 MD99620 (aka CX 22953) Hackintosh Mojave (UEFI Clover)

Hardware | Model | Status | Changes
------------ | ------------- | --- | ---
Device | MEDION Akoya E6418 MD99620 <br> CX 22953 | Working | &#45;
Motherboard | Pegatron D15D | Working | &#45;
Original OS | Windows 8.1 | Replaced | &#45;
Bits | x64 | Working | &#45;
BIOS | UEFI | Working | &#45;
Graphics | Intel HD Graphic 5500 (Broadwell) | Working | Patched
Graphics | Graphics: NVIDIA GeForce 940M (Maxwell) | [Not supported](https://dortania.github.io/GPU-Buyers-Guide/modern-gpus/nvidia-gpu.html#native-nvidia-gpus) | &#45;
Wifi & BT | RTL8723BE Realtek 802.11b/g/n | [Replaced](https://dortania.github.io/Wireless-Buyers-Guide/unsupported.html#supported-chipsets) | &#45;
Wifi & BT | Broadcom 802.11ac Network Adapter (BCM94352HMB) | Working | Patched
Processor | Intel Core i5-5200U CPU @ 2.20GH | Working | &#45;
Sound | NVIDIA Virtual Audio Device (Wave Extensible) (WDM) | &#45; | &#45;
Sound | Realtek High Definition Audio (ALC269 VC) | Working | Patched
LAN | Realtek PCIe GBE Family Controller Realtek RTL8168 | Working | Patched
Monitor | CMN15BE 1366 x 768 @ 60 Hz 15.3 inches | Working | &#45;
Webcam | Realtek Semiconductor Corp. 57da Built-In Video Camera | Working | &#45;
Trackpad | ELAN etd042F | Working | Patched
Keyboard | Numeric LATAM | Working | Patched
Brightness | &#45; | Working | Patched
Battery status | D15 | Working | Patched
Sensors | Proccesors & Devices | Working | Patched
USB | 2x3.0 <br> 2x2.0 | Working | &#45;
HDMI | &#45; | &#45; | &#45;
SD Card Reader | &#45; | &#45; | &#45;
---
## Extra devices needed for installation
* MacOS or Hackintosh PC: for creating installer
* USB 2.0 Flash Drive 16 GB: for USB installer
* [USB Wifi Stick MacOS compatible](https://dortania.github.io/Wireless-Buyers-Guide/types-of-wireless-card/usb.html): until Broadcom Wifi could be installed
* USB Keyboard MacOS compatible: until PS2 Keyboard is installed
* USB Mouse MacOS compatible: until PS2 Trackpad is installed
* [Wifi card MacOS compatible](https://dortania.github.io/Wireless-Buyers-Guide/unsupported.html#supported-chipsets)
---
## USB Stick Installer
1. With a Mackintosh or Hackintosh PC, download [MacOS Mojave installer](https://itunes.apple.com/us/app/macos-mojave/id1398502828?mt=12)
2. Create an account in [tonymacx86](https://www.tonymacx86.com/)
3. Sign in and download [Unibeast for Mojave](https://www.tonymacx86.com/resources/unibeast-9-3-0-mojave.449/)
4. Open Unibeast and install Mojave with UEFI Clover into the 16 GB USB pendrive (if doesn't work, try another pendrive)

---
## BIOS Settings
1. Update your [BIOS](http://www1.medion.de/downloads/index.pl?op=detail&id=15384&type=treiber&lang=uk)
---
## Install
---
## ACPI - DSDT
---
## LAN - Ethernet Realtek RTL8168 
---
## PS2 - Keyboard & Trackpad
---
## Wifi & BT - BCM94352HMB
---
## Graphic card - Intel HD 5500
---
## Battery & USB
---
## Sensors
---
## Brightness
---
## Sound & Mic - Realtek ALC 269
---
## USB Mouse
---
## Credits
* Thanks to [Diskmaker X creators](https://diskmakerx.com/) for [MacOS Installer](https://diskmakerx.com/download/) URLs
* Thanks to [TonyMac creators](https://www.tonymacx86.com/) for [Unibeast](https://www.tonymacx86.com/resources/categories/tonymacx86-downloads.3/) software
* Thanks to [Dortania](https://dortania.github.io/) for [USB Wireless](https://dortania.github.io/Wireless-Buyers-Guide/types-of-wireless-card/usb.html), [Nvidia GPU](https://dortania.github.io/GPU-Buyers-Guide/modern-gpus/nvidia-gpu.html#native-nvidia-gpus) and [Wireless chipset](https://dortania.github.io/Wireless-Buyers-Guide/unsupported.html#supported-chipsets) documentation
