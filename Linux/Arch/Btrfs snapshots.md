## [[Linux]] [[Arch]] [[compress and extract]] [[BTRFS]]

vim /etc/pacman.conf

================================
Install PARU /this is alternative for YAY
================================
cd Git
git clone https://aur.archlinux.org/paru
cd paru
makepkg -si
cd ~
paru
rm -fr paru
================================

sudo pacman -S rsync
paru -S snap-pac-grub snapper-gui

sudo umount /.snapshots
sudo rm -r /.snapshots
sudo snapper -c root create-config /
sudo btrfs subvolume delete /.snapshots
sudo mkdir /.snapshots
sudo mount -a 
sudo chmod 750 /.snapshots
sudo vim /etc/snapper/config/root

add rex to user
change clean up frequence
hourly=5
daily=7
the rest = 0

sudo systemctl enable --now snapper-timeline.timer
sudo systemctl enable --now snapper-cleanup.timer

sudo mkdir /etc/pacman.d/hooks
sudo vim /etc/pacman.d/hooks/50-bootbackup.hook

[Trigger]
Operation=Upgrade
Operation=Install
Operation=Remove
Type=Path
Target=boot/*

[Action]
Depends=rsync
Description=Backing up /boot...
When =PreTransaction
Exec = /usr/bin/rsync -a --delete /boot   /.bootbackup

sudo chmod a+rx /.snapshots
sudo chown :rex /.snapshots
39-25 start
41-24 complete
=========================================

recovery to an image

Recover from A ---> B
sudo snapper undochange A..B
A: pre #
B: post #

after broken!!
sudo btrfs subvol list /                'check  images
snapper ls                                       'check    current image will have "-"
sudo mount /dev/sda2 -o subvolid=5  /mnt
cd /mnt
ls -a
sudo mv @ @.broken

sudo btrfs subvol snapshot /mnt/@.snapshots/B/snapshot/    /mnt/@     

'B is the image you want to rollback
reboot

sudo btrfs subvol  list  /  | grep broken    'find broken image

sudo snapper --ambit classic rollback B
sudo grub-mkconfig -o /boot/grub/grub.cfg
reboot

sudo mount /dev/sda2 -o subvolid=5 /mnt
cd /mnt
ls -al
rm -fr @.broken
ls -al

=============
change Grub snapshot images Writeable!

sudo btrfs property set -ts /.snapshots/3/snapshot/  ro false


