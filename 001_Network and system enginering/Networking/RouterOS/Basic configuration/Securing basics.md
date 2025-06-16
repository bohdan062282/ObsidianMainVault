---
Category: Information
tags:
  - information
  - open
---

###### External links
*temporary, later my page:*
[Strong firewall rules](https://help.mikrotik.com/docs/spaces/ROS/pages/48660574/Filter)

---
## Description

---
## Securing basics
#### Access to a router
- ##### User and pass
	Add user and remove admin:
	```bash
	/user add name=myname password=mypassword group=full
	/user remove admin
	```
	
	MikroTik routers require password configuration, we suggest using a password generator tool to create secure and non-repeating passwords. With a secure password, we mean:
	
	- Minimum 12 characters;
	- Include numbers, Symbols, Capital and lowercase letters;
	- Is not a Dictionary Word or a Combination of Dictionary Words;
	- Note that quotes in the password require escaping;
	
	Set password and method to set a password for the current user:
	```bash
	/user set 0 password="!={Ba3N!40TуX+GvKBzjTLIUcx/,"
	(and)
	/password
	```

- ##### MAC-access
	RouterOS has built-in options for easy management access to network devices. The particular services should be shut down on production networks: **MAC-Telnet, MAC-WinBox,** and **MAC-Ping:**
	```bash
	/tool mac-server set allowed-interface-list=none
	/tool mac-server mac-winbox set allowed-interface-list=none
	/tool mac-server ping set enabled=no
	```

- ##### Neighbor Discovery
	MikroTik Neighbor discovery protocol is used to show and recognize other MikroTik routers in the network, and disable neighbor discovery on all interfaces:
	```bash
	/ip neighbor discovery-settings set discover-interface-list=none
	```

- ##### Bandwidth server
	A bandwidth server is used to test throughput between two MikroTik routers. Disable it in the production environment:
	```bash
	/tool bandwidth-server set enabled=no
	```

- ##### DNS Cache
	A router might have DNS cache enabled, which decreases the resolving time for DNS requests from clients to remote servers. In case DNS cache is not required on your router or another router is used for such purposes, disable it:
	```bash
	/ip dns set allow-remote-requests=no
	```

- ##### Other Clients Services
	RouterOS might have other services enabled (they are disabled by default RouterOS configuration). MikroTik caching proxy, socks, UPnP, and cloud services:
	```bash
	/ip proxy set enabled=no
	/ip socks set enabled=no
	/ip upnp set enabled=no
	/ip cloud set ddns-enabled=no update-time=no
	```

- ##### More Secure SSH access
	It is possible to enable more strict SSH settings (add aes-128-ctr and disallow hmac sha1 and groups with sha1) with this command:
	```bash
	/ip ssh set strong-crypto=yes
	```

---
#### Router interface
- ##### Ethernet/SFP interfaces
	It is good practice to disable all unused interfaces on your router, to decrease unauthorized access to your router:
	```bash
	/interface print
	/interface set x disabled=yes
	```

- ##### LCD
	Some RouterBOARDs have an LCD module for informational purposes, set a pin or disable it:
	```bash
	/lcd/pin/set pin-number=3659 hide-pin-number=yes
	
	/lcd/set enabled=no
	```

---
## Notes


---




