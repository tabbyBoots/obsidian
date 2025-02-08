## [[Linux]] [[PVE]] [[linux command]]

Look for the configuration file in the directory /etc/pve/qemu-server/. 
Is is named VM-NUMBER.conf. 
And edit it with, for example, nano and remove the lines that start with hostpci or put a # in front of those lines. 
You can also change the onboot setting and restart the host.

You can also restart the host and press the e-key and set intel_iommu or amd_iommu to off (or disable IOMMU in the host system BIOS), which should prevent any VM that uses passthrough from starting.

PS: You can reboot the host system with shutdown -r now or simply run reboot (as root).

https://forum.proxmox.com/threads/how-to-revert-pci-passthrough-via-cli.102368/