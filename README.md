# Hackintosh - MEDION Akoya E6418 aka CX 22953
This a documentation for creating a laptop MEDION Akoya E6418 MD99620 (aka CX 22953) Hackintosh Mojave (UEFI Clover)

Hardware | Model | Status | Changes
------------ | ------------- | --- | ---
Device | MEDION Akoya E6418 MD99620 <br> CX 22953 | Working | &#45;
Motherboard | Pegatron D15D | Working | &#45;
Original OS | Windows 8.1 | Replaced | &#45;
Bits | x64 | Working | &#45;
BIOS | UEFI | Working | &#45;
ACPI - DSDT | &#45; | Working | Patched
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
1. Turn off your PC and insert USB Stick Installer
3. Turn on your PC and press F2 for boot menu, choose pendrive (UEFI) to boot and press Enter.
5. In Clover menu, choose MacOS Installer
6. Search MacOS Utilies and choose Disk Utility
7. Erase the device where you will install MacOS
* Name: MacOS
* Format: AFPS
* Scheme: GUID Partition Map
8. Go back to MacOS Utilities and choose Installer
9. Install MacOS

---
## First Boot - Fix Kernel Panic
Into Clover menu:
1. Find IntelGFX and set it as 0x12345678
2. Find ACPI Patching and disable all

Once MacOS starts: Into EFI partition open Clover/config.plist with [Clover Configurator](https://www.tonymacx86.com/resources/clover-configurator.467/):
* IntelGFX: 0x12345678
* ACPI Patching: disable all.

---
## ACPI - DSDT
If you are an experienced developer, you can start with this [Patched DSDT.aml](https://github.com/lucasgabrielmoreno/Hackintosh_-MEDIONAkoyaE6418_CX22953/tree/main/ACPI). Read [Dortania documentation](https://dortania.github.io/Getting-Started-With-ACPI/ssdt-methods/ssdt-methods.html)

If you are newbie (like me), you might burn your motherboard with developer methods. So better this way:
1. Download [clover's config.plist](https://github.com/lucasgabrielmoreno/Hackintosh_-MEDIONAkoyaE6418_CX22953/tree/main/CLOVER)
2. Mount EFI partition with [EFI Mounter](https://www.tonymacx86.com/resources/efi-mounter-v3-1.447/)
3. Go to EFI/CLOVER/ and replace config.plist with [this config.plis](https://github.com/lucasgabrielmoreno/Hackintosh_-MEDIONAkoyaE6418_CX22953/blob/main/CLOVER/config.plist)
4. Reboot

---
## LAN - Ethernet Realtek RTL8168 
1. Download and Install the [latest RealtekRTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X/releases) with a kext installer like [Kext Utility](https://noobsplanet.com/index.php?resources/kext-utility.126/)
2. Reboot

---
## PS2 - Keyboard & Trackpad
1. Download [this version of Rehabman-Voodoo](https://bitbucket.org/RehabMan/os-x-voodoo-ps2-controller/downloads/RehabMan-Voodoo-2018-0506.zip)
2. Extract and go to "Release" Folder. Replace VoodooPS2Controller.kext file with the [latest VoodooPS2Controller](https://github.com/acidanthera/VoodooPS2/releases)
3. Open terminal
4. Type:

`sudo su`

6. Drag and drop "RehabMan-Voodoo-2018-0506" folder to terminal
7. Type: 

`sudo cp org.rehabman.voodoo.driver.Daemon.plist /Library/LaunchDaemons`

`cd Release`

`sudo cp -R VoodooPS2Controller.kext /System/Library/Extensions/`

`sudo cp VoodooPS2Daemon /usr/bin`

`sudo touch /System/Library/Extensions/ && sudo kextcache -u /`

`sudo reboot`

---
## LATAM(Latinoamerican) Windows Keyboard 
1. Download and Install [Ukelele](https://software.sil.org/ukelele/)
2. Go to Latam Keyboard(https://github.com/neosergio/Latam-Keyboard) and download Code as Zip
3. Copy zip folder content into "System/Library/Keyboard Layouts/" folder
4. Open "Latam_A_white.keylayout" with Ukelele
5. Fie > Install > Show Organizer
6. Set Folder > "Latam-Keyboard-master" into "System/Library/Keyboard Layouts/"
7. Drag and drop "Latam_A_white.keylayout"(and every file) to Installed for Current User
8. Reboot
9. Go to Keyboard > Input Sources > Remove all keyboard languajes that doesn't fit with yout laptop keyboard. If you can't remove some of them (like ISO Español) add more languajes and then remove all of them.

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
## Wifi & BT - BCM94352HMB
1. Download [BrcmPatchRAM last release](https://github.com/acidanthera/BrcmPatchRAM/releases)
2. Download [Rehabman-PCIID](https://bitbucket.org/RehabMan/os-x-fake-pci-id/downloads/RehabMan-FakePCIID-2018-1027.zip) (extract Release folder)
3. Install only this kexts with a kext installer like [Kext Utility](https://noobsplanet.com/index.php?resources/kext-utility.126/)
* BrcmFirmwareRepo.kext
* BrcmPatchRAM.kext
* BrcmPatchRAM2.kext
* FakePCIID_Broadcom_WiFi.kext
* FakePCIID.kext

4. From EFI partition, open Clover/config.plist with [Clover Configurator](https://www.tonymacx86.com/resources/clover-configurator.467/) and go to "Kernel and Kexts patches", and add:

Name | Find | Replace
------------ | ------------- | ---
AirPortBrcm4360 | 81f952aa00007529 | 81f952aa00006690


5. Open terminal and type:

`sudo kextcache -i /`

`sudo reboot`

---
## Graphic card - Intel HD 5500
1. You need ACPI - DSDT patched with Clover or .aml method.
2. Download [Lilu](https://github.com/acidanthera/Lilu/releases) last release.
3. Download [WatheverGreen](https://github.com/acidanthera/whatevergreen/releases) last release.
4. Mount EFI partition with [EFI Mounter](https://www.tonymacx86.com/resources/efi-mounter-v3-1.447/)
5. Go to this folder EFI/CLOVER/kexts/Other and paste Lilu and WatheverGreen kexts 
6. From EFI partition, open Clover/config.plist with [Clover Configurator](https://www.tonymacx86.com/resources/clover-configurator.467/) and go to:
* Devices, set IntelGFX: 0x12345678
* Graphics, set VRAM: 2400
* Graphics, set Ig-platform-id: 0x16260006
* Kernel and Kext Patches:

Name | Find | Replace
------------ | ------------- | ---
AppleIntelSKLGraphicsFramebuffer| 8945C839C7764F | 8945C839C7EB4

7. File > Save > Exit
8. Open terminal
`sudo kextcache -i /`
9. Reboot

---
## Battery & USB
1. Download [VirtualSMC](https://github.com/acidanthera/virtualsmc/releases) last release.
2. Download [USBInjectAll](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/RehabMan-USBInjectAll-2018-1108.zip).
3. Mount EFI partition with [EFI Mounter](https://www.tonymacx86.com/resources/efi-mounter-v3-1.447/)
4. Go to this folder EFI/CLOVER/kexts/Other and paste all kexts downloaded: VirtualSMC, SMCBatteryManager, SMCDellSensors, SMCLightSensor, SMCProcessor, SMCSuperIO and USBInjectAll.
5. If there is a FakeSMC.kext into EFI/CLOVER/kexts/Other, remove it.
6. Reboot
7. Go to: Systema preferences > Energy Saver > Show battery status in menu bar

---
## Sensors
1. Download and install [Intel Powe Gadget](https://software.intel.com/content/www/us/en/develop/articles/intel-power-gadget.html)
2. Download and install [HWMonitorSMC2](https://github.com/CloverHackyColor/HWMonitorSMC2/releases) and activate options inside.
3. Downlaod and install [HWSensors](https://sourceforge.net/projects/hwsensors/) but deactivating FakeSMC and all FakeSMC options.
4. Reboot

---
## Brightness
1. Download [SSDT-PNLF](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-PNLF.aml)
2. Mount EFI partition with [EFI Mounter](https://www.tonymacx86.com/resources/efi-mounter-v3-1.447/)
4. Go to this folder EFI/CLOVER/ACPI/Patched/ and paste SSDT-PNLF.aml
5. Install [Brightness Slider](https://apps.apple.com/us/app/brightness-slider/id456624497?mt=12)

---
## Sound & Mic - Realtek ALC 269

---
## USB Mouse

---
## Grub - Multiboot
`menuentry "MacOS" {`

`search --file --no-floppy --set=root /EFI/CLOVER/CLOVERX64.efi`

`chainloader /EFI/CLOVER/CLOVERX64.efi`

`}`

---
## Credits
* Thanks to [Diskmaker X creators](https://diskmakerx.com/) for [MacOS Installer](https://diskmakerx.com/download/) URLs
* Thanks to [TonyMac creators](https://www.tonymacx86.com/) for [Unibeast](https://www.tonymacx86.com/resources/categories/tonymacx86-downloads.3/) software
* Thanks to [Dortania](https://dortania.github.io/) for [USB Wireless](https://dortania.github.io/Wireless-Buyers-Guide/types-of-wireless-card/usb.html), [Nvidia GPU](https://dortania.github.io/GPU-Buyers-Guide/modern-gpus/nvidia-gpu.html#native-nvidia-gpus), [Wireless chipset](https://dortania.github.io/Wireless-Buyers-Guide/unsupported.html#supported-chipsets) and [BIOS settings](https://dortania.github.io/OpenCore-Install-Guide/config.plist/coffee-lake.html#intel-bios-settings) documentation
* Thanks to [Rehabman](https://github.com/RehabMan) for [HD5500 config.plist](https://github.com/RehabMan/OS-X-Clover-Laptop-Config), [Voodoo PS2](https://bitbucket.org/RehabMan/os-x-voodoo-ps2-controller/downloads/), [FakePCIID](https://bitbucket.org/RehabMan/os-x-fake-pci-id/downloads/), [USBInjectAll](https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/)
* Thanks to [Mieze](https://github.com/Mieze/RTL8111_driver_for_OS_X) for [RealtekRTL8111](https://github.com/Mieze/RTL8111_driver_for_OS_X)
* Thanks to [Noobsplanet](https://noobsplanet.com) for [Keyboard PS2 Tutorial](https://youtu.be/EFSfNDdo1VE), [Graphic card tutorial](https://noobsplanet.com/index.php?threads/intel-hd-5300-5500-and-6000-graphics-fix-for-hackintosh.13/)
* Thanks to [Adidanthera](https://github.com/acidanthera) for [BrcmPatchRAM](https://github.com/acidanthera/BrcmPatchRAM), [VirtualSMC](https://github.com/acidanthera/VirtualSMC)
* Thanks to [AIOBoot](https://www.aioboot.com) for [Grub config](https://www.aioboot.com/en/add-clover-to-grub/)
* Thanks to [Neosergio](https://github.com/neosergio) for [Latam Keyboard](https://github.com/neosergio/Latam-Keyboard)
* Thanks to [SIL Ls Dev](https://github.com/sillsdev) for [Ukelele](https://software.sil.org/ukelele/)
* Thanks to [Lwouis](https://github.com/lwouis) for [Alt-Tab](https://alt-tab-macos.netlify.app)
* Thanks to [IMHO Production](https://www.youtube.com/channel/UCyFSS3f8yn8aEv264lufdxg) for [Battery fix](https://www.youtube.com/watch?v=jvuIpX2MUCk) tutorial.
* Thanks to [Femi Ojeyemi](https://www.youtube.com/channel/UCa0i_qRkhNK_f_4ODT2FWlw) for [Fix brightness tutorial](https://youtu.be/ZC0NHWc8ibE)
