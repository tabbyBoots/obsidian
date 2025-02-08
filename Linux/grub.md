[[linux]] [[linux command]] [[grub]]
- [[grub]]
	- grub-install --target=x86_64-efi --root-directory=/mnt --efi-directory=/mnt/boot --bootloader-id=GRUB
	- if you just type cfdisk, only the default hard drive table will be shown...
	  if you got a 2nd hard drive such as "/dev/hdb" you must specify it with the command
	  "cfdisk /dev/hdb"
-
	- edit /etc/default/grub add or uncomment GRUB_DISABLE_OS_PROBER=false save that file then run sudo update-grub or sudo grub-mkconfig -o /boot/grub/grub.cfg
-
	- grub conf
	  /etc/default/grub
-
- sudo dd if=out/archlinux*.iso of=/dev/sdb bs=1M
-
- Listing network interfaces
  ls /sys/class/net
- Enabling and disabling network interfaces
  ip link set interface up|down
- https://wiki.t2linux.org/distributions/arch/installation/