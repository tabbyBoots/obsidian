-[[DNS]]
- Edit DNS server
	- sudo nano /etc/resolv.conf
	  nameserver 9.9.9.9
	  nameserver 142.112.112.112
	- prevent overwritten
	  chattr +i /etc/resolv.conf