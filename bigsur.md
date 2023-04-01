# Big Sur OpenCore

- OpenCore 0.6.3
- [OpenCore Configurator 2.16.0.0 for OpenCore 0.6.3](https://mackie100projects.altervista.org/occ-changelog-version-2-16-0-0/)

## USB Stick Installer 
1. Download Big Sur: https://apps.apple.com/us/app/macos-big-sur/id1526878132?mt=12
2. Open terminal:
```
sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /Volumes/Untitled
```
3. Mount EFI partition and paste [Big Sur OpenCore EFI](https://github.com/lucasgabmoreno/Hackintosh-MEDION-Akoya-E6418-CX-22953/tree/main/Big%20Sur%20OpenCore%20EFI) content.

## Install
1. Boot USB and install
2. Mount EFI partition and paste [Big Sur OpenCore EFI](https://github.com/lucasgabmoreno/Hackintosh-MEDION-Akoya-E6418-CX-22953/tree/main/Big%20Sur%20OpenCore%20EFI) content.


---

## Grub - Multiboot
```
menuentry "MacOS" --class macosx {
	search --file --no-floppy --set=root /EFI/OC/OpenCore.efi
	chainloader /EFI/OC/OpenCore.efi
}
```
