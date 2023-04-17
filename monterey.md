# Monterey OpenCore

- OpenCore 0.8.8

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
