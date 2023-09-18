# Mojave Clover

## Extra devices needed for installation
* MacOS or Hackintosh PC: for creating installer
* USB 2.0 Flash Drive 16 GB: for USB installer
* [USB Wifi Stick MacOS compatible](https://dortania.github.io/Wireless-Buyers-Guide/types-of-wireless-card/usb.html): until Broadcom Wifi could be installed
* USB Keyboard MacOS compatible: until PS2 Keyboard is installed
* USB Mouse MacOS compatible: until PS2 Trackpad is installed
* [Wifi card MacOS compatible](https://dortania.github.io/Wireless-Buyers-Guide/unsupported.html#supported-chipsets)

---

## USB Stick Installer 
1. Create an account in [tonymacx86](https://www.tonymacx86.com/)
2. With a Mac or Hackintosh PC, download [MacOS Mojave installer](https://apps.apple.com/us/app/macos-mojave/id1398502828?mt=12)
3. Sign into TonyMac and download [Unibeast for Mojave](https://www.tonymacx86.com/resources/unibeast-9-3-0-mojave.449/)
4. Go to [Diskmaker X](https://diskmakerx.com/download/) and download [Diskmaker for Mojave](http://diskmakerx.com/downloads/DiskMaker_X_803.dmg)
5. First pass: Install and open Diskamaker X and create Mojave USB pendrive.
6. Second pass: Open Unibeast and install Mojave with UEFI Clover into the USB pendrive.

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
1. Download [Lilu](https://github.com/acidanthera/Lilu/releases) last release.
2. Download [WatheverGreen](https://github.com/acidanthera/whatevergreen/releases) last release.
3. Mount EFI partition with [EFI Mounter](https://www.tonymacx86.com/resources/efi-mounter-v3-1.447/)
4. Go to this folder EFI/CLOVER/kexts/Other and paste Lilu and WatheverGreen kexts 
5. From EFI partition, open Clover/config.plist with [Clover Configurator](https://www.tonymacx86.com/resources/clover-configurator.467/) and go to:
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

## Brightness
1. Download [SSDT-PNLF](https://github.com/dortania/Getting-Started-With-ACPI/blob/master/extra-files/compiled/SSDT-PNLF.aml)
2. Mount EFI partition with [EFI Mounter](https://www.tonymacx86.com/resources/efi-mounter-v3-1.447/)
4. Go to this folder EFI/CLOVER/ACPI/Patched/ and paste SSDT-PNLF.aml
5. Install [Brightness Slider](https://apps.apple.com/us/app/brightness-slider/id456624497?mt=12)

---

## Sound & Mic - Realtek ALC 269
1. Download [AppleALC](https://github.com/acidanthera/AppleALC/releases) last release.
2. Mount EFI partition with [EFI Mounter](https://www.tonymacx86.com/resources/efi-mounter-v3-1.447/)
3. Go to this folder EFI/CLOVER/kexts/Other and paste AppleALC kext
4. From EFI partition, open Clover/config.plist with [Clover Configurator](https://www.tonymacx86.com/resources/clover-configurator.467/) and go to:
* ACPI > DSDT > change B0D3 to HDAU > Disabled
* ACPI > Fixes > FixHDA > NO
* ACPI > Fixes > AddHDMI > NO
* Devices > UseIntelHDMI > NO
* Devices > Audio Inject > No
* Devices > Audio Inject > ResetHDA
* Boot > Arguments > + >alcid=35
* Devices > Properties > PciRoot(0x0)/Pci(0x1B,0x0) > layout-id=35
6. Reboot

---

## USB Mouse
1. Open terminal

`defaults write .GlobalPreferences com.apple.mouse.scaling -1`

2. Install [Steel Series](https://ar.steelseries.com/engine)

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

## Grub - Multiboot
```
menuentry "MacOS" {
search --file --no-floppy --set=root /EFI/CLOVER/CLOVERX64.efi
chainloader /EFI/CLOVER/CLOVERX64.efi
}
