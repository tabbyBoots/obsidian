## [[Linux]] [[Arch]] [[compress and extract]]

reflector -c Taiwan --verbose --latest 5 --sort rate --save /etc/pacman.d/mirrorlist

timedatectl set-ntp true

---------------------------------------------------
partition type 1
---------------------------------------------------
mkfs.fat -F32 /dev/sda1
mkfs.btrfs /dev/archlvm/root -f
mkfs.btrfs /dev/archlvm/home -f
----------------------------------------------------


----------------------------------------------------
partition type2
----------------------------------------------------
mount /dev/sda1 /mnt --mkdir
btrfs su cr /mnt/@
btrfs su cr /mnt/@home
btrfs su cr /mnt/@snapshots
btrfs su cr /mnt/@var_log

umount /mnt

mount -o noatime,compress=lzo,space_cache=v2,subvol=@ /dev/sda2 /mnt
mkdir -p /mnt/{boot,home,.snapshots,var_log}
mount -o noatime,compress=lzo,space_cache=v2,subvol=@home /dev/sda2 /mnt/home
mount -o noatime,compress=lzo,space_cache=v2,subvol=@snapshots /dev/sda2 /mnt/.snapshots
mount -o noatime,compress=lzo,space_cache=v2,subvol=@var_log /dev/sda2 /mnt/var_log
mount /dev/sda1 /mnt/boot
15-04
pacstrap

8-25 check grub encryption

encryption:
cryptsetup luksFormat /dev/sda3 --type luks2
YES
cryptsetup open /dev/sda3 root

pacstrap /mnt base linux linux-firmware linux-headers man-db man-pages texinfo lvm2 vim sudo grub efibootmgr dhcpcd networkmanager os-prober git reflector intel-ucode bash-completion terminus-font firewalld

gpart iw kitty-terminfo nfs-utils nmap openssh openvpn 
qemu-guest-agent rsync tmux 
filezilla firefox flatpak mpv vlc qbittorrent



genfstab -U /mnt >> /mnt/etc/fstab
arch-chroot /mnt
ln -sf /usr/share/zoneinfo/Region/City /etc/localtime
hwclock --systohc

Edit /etc/locale.gen 
locale-gen
echo LANG=en_US.UTF-8 >> /etc/locale.conf
echo archo >> /etc/hostname

vim /etc/hosts
127.0.0.1	localhost
::1	localhost
127.0.1.1	archlvm.localdomain	archlvm

mkinitcpio -P
passwd
systemctl enable NetworkManager

vim /etc/mkinitcpio.conf
Hook=(base udev autodetect keyboard keyboard keymap modconf block lvm2 encrypt filesystems fsck)

mkinitcpio -P

vim /etc/default/grub
r !blkid

root --> UUID="f65a3d2f-e1a7-4c13-b463-630095ad81e3"

...quiet cryptdevice=UUID=f65a3d2f-e1a7-4c13-b463-630095ad81e3:root root=/dev/mapper/root

delete blockid

---------------------
20-20 do this if swap partition is made within btrfs partition
vim /etc/crypttab
vim /etc/fstab
/dev/mapper/swap none swap sw 0 0
---------------------
grub-install --efi-directory=/boot --bootloader-id=GRUB
grub-mkconfig -o /boot/grub/grub.cfg
-----------------------------------------------------
keyfolder
mkdir -m 700 /etc/juks-keys
dd if=/dev/random of=/etc/luks-keys/home bs=1 count=256 status=progress
dd if=/dev/random of=/etc/luks-keys/.snapshots bs=1 count=256 status=progress
----------------------------------------------------
cryptsetup luksFormat -v /dev/vg-group/pv /etc/luks-keys/home --type luks2

cryptsetup -d /etc/luks-keys/home open /dev/vg-group/pv home
34-48
-----------------------------------------------------

Btrfs Swap

create:
btrfs filesystem mkswapfile --size 4g --uuid clear /swap/swapfile

activate:
swapon /swap/swapfile

edit fstab
/swap/swapfile none swap defaults 0 0


umount /mnt

check /etc/fstab       noatime, compress=zstd

mount -o noatime,compress=lzo,space_cache=v2,subvol=@ /dev/sda2 /mnt
mkdir -p /mnt/{boot,home,.snapshots,var_log}
mount -o noatime,compress=lzo,space_cache=v2,subvol=@home /dev/sda2 /mnt/home
mount -o noatime,compress=lzo,space_cache=v2,subvol=@snapshots /dev/sda2 /mnt/.snapshots
mount -o noatime,compress=lzo,space_cache=v2,subvol=@var_log /dev/sda2 /mnt/var_log
mount /dev/sda1 /mnt/boot

pacstrap /mnt base linux linux-firmware vim intel-ucode

compression=zstd will do
----------------------------------------------------
arch-chroot /mnt
cd 
mount /dev/archlvm/root /mnt/root --mkdir
mount /dev/archlvm/home /mnt/home --mkdir
mount /dev/sda1 /mnt/boot --mkdir

pacstrp /mnt/root base linux linux-firmware intel-ucode vim git lvm2 
10.3
9.16

fallocate -l 4GB /swapfile
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile

genfstab -U /mnt/root >> /mnt/root/etc/fstab

cat fstab
relatime---> noatime
compress=zstd
space_cache=v2 ---> redundant so delete it.

echo LANG=en_US.UTF-8 >> /etc/locale.conf

vim /etc/hosts
127.0.0.1	localhost
::1	localhost
127.0.1.1	archlvm.localdomain	archlvm

pacman -S grub efibootmgr networkmanager os-prober git reflector 

mkdir /boot/grub

grub-mkconfig -o /boot/grub/grub.cfg
nano /etc/mkinicpio.conf
mkinitcpio -P

grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB

====================
POST installation

useradd -mG wheel rex
passwd rex
EDITOR=vim visudo
26-34
-------------------------------------
su rex
cd ~
mkdir Git
cd Git
git clone https://github.com/stephenstechtalks/ArchLinux
12-06

sudo pacman -Syy
sudo pacman -Syu

pacman -S --needed - < ArchISO.....
pacman -S --needed - < Driver.....
pacman -S --needed - < Net.....
pacman -S --needed - < Fonts.....
pacman -S --needed - < Print.....
pacman -S --needed - < MMedia.....
pacman -S --needed - < Xorg.....
pacman -S --needed - < KDE.....
pacman -S --needed - < Apps.....

systemctl enable avahi-daemon
systemctl enable haveged.service
systemctl enable firewalld.service
systemctl enable sddm.service
systemctl enable NetworkManager
systemctl enable sshd
systemctl enable upower
19-01

id rex
usermod -aG \
sys,adm,network,scanner,power,uucp,audio,lp,rfkill,video,storage,optical,users \
rex
20-21

==================

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

install yay
35-04
====================
vim /etc/pacman.conf

Install PARU /this is alternative for YAY

cd Git
git clone https://aur.archlinux.org/paru
cd paru
makepkg -si
cd ~
paru
rm -fr paru

paru timeshift
review --> finished click "q"
select autosnap

use timeshift to create 1st snapshot

paru -S grub-btrfs
sudo grub-mkconfig -o /boot/grub/grub.cfg
====================
yay -S snap-pac-grub snapper-gui

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

sudo pacman -S rsync
sudo chmod a+rx /.snapshots
sudo chown :rex /.snapshots
39-25 start
41-24 complete

====================
openbox

sudo pacman -S --needed xorg xorg-xinit openbox ttf-dejavu ttf-liberation xterm xfce4-terminal obconf lxappearance-obconf menumaker tint2

cd ~
cp /etc/X11/xinit/xinitrc .xinitrc

vim .xinitrc
exec openbox-session

mkdir .config/openbox

cp -a /etc/xdg/openbox/. .config/openbox/

-----
/dev/mapper/archlvm-root:
UUID="8c02ac61-10a4-44ad-b27f-4293670b50b0"
-----

