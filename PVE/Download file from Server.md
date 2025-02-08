## [[Linux]] [[PVE]] [[compress and extract]]

shutdown  lxc
type:
pct mount lxc_id
(such as "pct mount 101")

-r meaning download the whole folder
pscp -r root@192.168.1.201:/var/lib/lxc/101/rootfs/Downloads ~/Downloads
