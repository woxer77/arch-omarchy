# Omarchy Installation
lsblk
cfdisk /dev/<disk arch to be installed>nvme0n1
Free space -> New -> 1G -> Type EFI
Free space -> New -> All -> Write -> Quit
lsblk
mkfs.fat -F32 /dev/<1G>nvme0n1p5
mkfs.btrfs (optional -f flag if needed)  /dev/<All>nvme0n1p6
lsblk
mount /dev/nvme0n1p6 /mnt
mkdir /mnt/boot
mount /dev/nvme0n1p5 /mnt/boot
lsblk
archinstall
Disk configuration -> Partition -> Pre-mounted configuration -> /mnt
Bootloader -> limine
Hostname -> omarchy
Root password -> ...
User account -> woxer -> pass ... -> sudo +
Applications -> Bluetooth, pipewire
Profile -> Minimal
Network configuration -> Copy ISO network ...
Timezone -> Europe/Kyiv
Install

Choose reboot system
Change boot priority to Limine (not Windows Boot Manager or flash)

launch linux
sudo pacman -Syu
sudo pacman -S git curl nano
curl -fsSL https://omarchy.org/install | bash
reboot

launch linux
sudo limine-scan -> select Windows bootloader
change limine display time from 3s to (n)sec -> sudo nano /boot/limine.conf
