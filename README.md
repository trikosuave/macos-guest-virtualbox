## Semi-automatic installer of macOS on VirtualBox

### supports macOS Catalina (10.15), Mojave (10.14), and High Sierra (10.13)

The script is semi-automatic and requires a little user interaction. Most of the time the user simply has to press enter. There is one step where the user has to choose between [C]atalina, [M]ojave, or [H]igh Sierra, and a couple of instances where the user has to choose whether to delete or keep temporary files and previous installations.

The goal of the script is to allow for a very easy installation without any closed-source additions or extra bootloaders.

Tested on Cygwin and WSL, should work on most Linux distros.

## iCloud and iMessage connectivity

iCloud, iMessage, and other connected Apple services require a valid device name and serial number, board ID and serial number, and other genuine (or genuine-like) Apple parameters, some of which are not passed to the virtual machine by VirtualBox. These parameters may be set by [attaching an ISO of the bootloader Clover](https://sourceforge.net/projects/cloverefiboot/files/Bootable_ISO/) and changing the parameters on the Clover SMBIOS options screen, however this script is not compatible with booting macOS from Clover on VirtualBox.

## Storage size

The script assigns the minimum required storage size for the installation. After the installation is complete, the storage size may be increased. First increase the virtual disk image size through VirtualBox Manager or `VBoxManage`, then in Terminal in the virtual machine run `sudo diskutil repairDisk disk0`, and then from Disk Utility delete the "Free space" partition, allowing the system APFS container to take up the available space.

## Unsupported features

Developing and maintaining VirtualBox or macOS features is beyond the scope of this script. Some features may behave unexpectedly, such as USB device support, [audio support](https://github.com/chris1111/VoodooHDA-2.9.2-Clover-V13/releases), and other features.

## Dependencies

* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)≥6 with Extension Pack
* `Bash`≥4 (run on Windows through [Cygwin](https://cygwin.com/install.html) or WSL)
* `coreutils`, `unzip`, `wget` (install through package manager)
* `dmg2img` (install through package manager on Linux or WSL; let the script download it automatically on Cygwin)
