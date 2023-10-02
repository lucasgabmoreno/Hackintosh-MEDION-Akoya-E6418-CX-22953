# Hackintosh - MEDION Akoya E6418 aka CX 22953

![screenshot](/screenshot.png "Screenshot")

- OpenCore 0.8.8
- MacOS Monterey

### Working
- iGPU Intel 5500 Broadwell
- Wifi & BT Broadcom BCM94352HMB
- Audio ALC269 VC (alcid=35)
- LAN Realtek RTL8168
- Trackpad & Keyboard
- Brightness (keepsyms=1 debug=0x100 -wegnoegpu)

### Not Working
- dGPU NVIDIA 940M Maxwell: [Not supported](https://dortania.github.io/GPU-Buyers-Guide/modern-gpus/nvidia-gpu.html#native-nvidia-gpus)
- Wifi & BT Realtek RTL8723BE: [Replaced](https://dortania.github.io/Wireless-Buyers-Guide/unsupported.html#supported-chipsets)
- SMBUS: PCI0.D00C

---

## BIOS
1. Using Windows, update your BIOS with [official Medion BIOS updater](http://www1.medion.de/downloads/index.pl?op=detail&id=15384&type=treiber&lang=uk)
2. Into the BIOS (turn on the computer and press F2) change settings to:
   
| Var   | Status |
|:---|:---|
| Secure Boot | Disabled|
| Fast Boot | Disabled |
| PXE Boot | Disabled |
| SATA Mode Selection | AHCI |

3. Press F10: Save & Exit

---

## Installer 
1. Download Monterey: https://apps.apple.com/us/app/macos-monterey/id1576738294?mt=12
2. Open terminal:
```
sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled
```
3. Mount EFI partition and paste [Monterey OpenCore EFI](https://github.com/lucasgabmoreno/Hackintosh-MEDION-Akoya-E6418-CX-22953/tree/main/EFI) content.

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
