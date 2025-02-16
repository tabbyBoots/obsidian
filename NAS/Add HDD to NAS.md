## [[NAS command]]


sudo mount /opt/NAS_storage

====================
apt install lshw

lshw -class disk -class storage

ls -l /dev/disk/by-id/

sda     ata-ST4000VN006-3CW104_ZW625CCV
sdb     ata-ST4000VN006-3CW104_ZW625KLT

sdb     ata-ST4000VN006-3CW104_ZW625MQT
sdc     ata-ST4000VN006-3CW104_ZW625DSY

sde     ata-WDC_WD40EFPX-68C6CN0_WD-WX42D636R93A
sdf      ata-WDC_WD40EFPX-68C6CN0_WD-WX42D63HKSED

Type this cmd in PVE shell, not truenas shell
qm set 101 -scsi1 /dev/disk/by-id/ata-ST3000DM001-1CH166_Z1F41BLC

101---> modify to match VM ID
-scsi1--> moddify to add new scsi
Z1F41BLC--> modify to match HDD serial number

backup conf
cp /etc/pve/qemu-server/101.conf /root/101_TrueNAS_backup.conf



