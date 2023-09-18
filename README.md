# Hackintosh - MEDION Akoya E6418 aka CX 22953

- OpenCore 0.8.8
- MacOS Monterey

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


### Not Working
- NVIDIA GeForce 940M (Maxwell): [Not supported](https://dortania.github.io/GPU-Buyers-Guide/modern-gpus/nvidia-gpu.html#native-nvidia-gpus)
- RTL8723BE Realtek 802.11b/g/n: [Replaced](https://dortania.github.io/Wireless-Buyers-Guide/unsupported.html#supported-chipsets)

---


## BIOS Settings
1. Using Windows, update your BIOS with [official Medion BIOS updater](http://www1.medion.de/downloads/index.pl?op=detail&id=15384&type=treiber&lang=uk)
2. Into the BIOS (turn on the computer and press F2) change settings to:
| Var   | Status |
|:---|:---|
| Intel Virtualization Technology | Enable |
| Legacy USB Support  Enable |
| USB Charger | Disabled |
| TPM Device | Disabled |
| Secure Boot | Disabled|
| Secure Boot Mode | Enable |
| Fast Boot | Disabled |
| CSM Support | Enabled |
| PXE Boot | Disabled |
| SATA Mode Selection | AHCI |
3. Press F10: Save & Exit

---

## USB Stick Installer 
1. Download Monterey: https://apps.apple.com/us/app/macos-monterey/id1576738294?mt=12
2. Open terminal:
```
sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled
```
3. Mount EFI partition and paste [Monterey OpenCore EFI](https://github.com/lucasgabmoreno/Hackintosh-MEDION-Akoya-E6418-CX-22953/tree/main/Monterey%20OpenCore%20EFI) content.

## Install
1. Boot USB and install
2. Mount EFI partition and paste [Monterey OpenCore EFI](https://github.com/lucasgabmoreno/Hackintosh-MEDION-Akoya-E6418-CX-22953/tree/main/Monterey%20OpenCore%20EFI) content.


---

## Grub - Multiboot
```
menuentry "MacOS" --class macosx {
	search --file --no-floppy --set=root /EFI/OC/OpenCore.efi
	chainloader /EFI/OC/OpenCore.efi
}
```
---


## References
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
* [Vejtarn](https://github.com/Vejtarn/Hackintosh-Asus-X555LJ-Monterey)
