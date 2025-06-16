---
Category: Instruction
tags:
  - instruction
  - open
---
---
###### External links
- 
## Description
There are two types of routers:
- Routers with default configuration.
- Routers without default configuration. In cases where no specific configuration is present, the IP address 192.168.88.1/24 is assigned to ether1, combo1, sfp1, or MGMT/BOOT.
When connecting the first time to the router with the default username **admin** and **no password** (or, for some models, check user and wireless passwords on the sticker).

- *Print можно дополнить фильтром по параметру, например: /ip firewall filter print where chain=forward*

---
## Manual
#### Def conf
The easiest method to ensure a completely clean router is to run the CLI command:
```bash
/system reset-configuration no-defaults=yes skip-backup=yes
```
##### [[Configuration Management#Reset configuration]]
---
#### Configuring IP Access
- Создание бриджа
- Создание порта и добавление в бридж
- Добавление айпи для себя на интерфейсе
```bash
/interface bridge add name=bridge1
/interface bridge port add interface=ether2 bridge=bridge1
/ip address add address=192.168.88.1/24 interface=bridge1`
```
*Вот много где можно манипулировать с интерфейслистами, но как раз адрес роутера возможен нолько на физический интерфейс ну или на бридж или порт*

---
#### DHCP server
To simplify and expedite this process, we'll execute the **setup** command.
*По сути сетап еще сам создает айпипул и нетворк и их использует*
```bash
/ip dhcp-server setup [enter]
```
*Сеть указывается через слеш - `192.168.88.0/24`*
*Пул адресов через тире - `192.168.88.2-192.168.88.254`*
*По идее через запятую можно параметры вписывать*
*Время в конце можно указать m-для минут, а так по дефолту в секеундах*

---
#### Configuring Internet Connection
- ##### Dynamic Public IP
	Dynamic address configuration is the easiest option. Simply set up a DHCP client on the public interface. The DHCP client will obtain information from your Internet Service Provider (ISP), such as an IP address, DNS servers, NTP servers, and default route, making the setup process straightforward for you.
	```bash
	/ip dhcp-client add disabled=no interface=ether1
	```

- ##### Static Public IP
	To configure this in RouterOS, we'll manually add an IP address, add a default route with a provided gateway, and set up a DNS server
	```bash
	/ip address add address=1.2.3.100/24 interface=ether1
	/ip route add gateway=1.2.3.1
	/ip dns set servers=8.8.8.8
	```

- ##### PPPoE Connection
```bash
	/interface pppoe-client add disabled=no interface=ether1 user=me password=123 add-default-route=yes use-peer-dns=yes`
```

---
#### Protecting the router

- ##### [[Securing basics#User and pass]]

- ##### Interface list
	Создать интерфейс-лист и добавить в интерфейс-лист интерфейс:
	```bash
	/interface list add name=LAN
	/interface list member add list=LAN interface=bridge1
	```

- ##### [[Securing basics#MAC-access]]

- ##### [[Securing basics#Neighbor Discovery]]

- ##### IP Connectivity Access
	To add allowed addresses for user:
	```bash
	/user set 0 address=x.x.x.x/yy
	```
	*x.x.x.x/yy - your IP or network subnet that is allowed to access your router*
	
	IP connectivity on the public interface must be limited in the firewall. We will accept only ICMP(ping/traceroute), IP Winbox, and ssh access:
	```bash
	/ip firewall filter add chain=input action=accept connection-state=established,related,untracked comment="accept established,related,untracked"
	add chain=input action=drop connection-state=invalid comment="drop invalid"
	add chain=input in-interface=ether1 action=accept protocol=icmp comment="accept ICMP"
	add chain=input in-interface=ether1 action=accept protocol=tcp port=8291 comment="allow Winbox";
	add chain=input in-interface=ether1 action=accept protocol=tcp port=22 comment="allow SSH";
	add chain=input in-interface=ether1 action=drop comment="block everything else";
	```
	
	Most of RouterOS administrative tools are configured at  the /ip service menu
	- Keep only secure ones
	- Change default service ports, this will immediately stop most of the random SSH brute force login attempts
	```bash
	/ip service disable telnet,ftp,www,api
	/ip service set ssh port=2200
	```
	
	Additionally, each service can be secured by allowed IP address or address range(the address service will reply to), although more preferred method is to block unwanted access in firewall because the firewall will not even allow to open socket
	```bash
	/ip service set winbox address=192.168.88.0/24
	```

- ##### Other Services
	- [[Securing basics#Bandwidth server]]
	- [[Securing basics#DNS Cache]]
	- [[Securing basics#Other Clients Services]]
	- [[Securing basics#LCD]]
	- [[Securing basics#Ethernet/SFP interfaces]]
	- [[Securing basics#More Secure SSH access]]

---
#### NAT Configuration
```bash
/ip firewall nat
add chain=srcnat out-interface=ether1 action=masquerade
```

- ##### Port Forwarding
	After a quick search on Google, we find out that RDP runs on TCP port 3389. Now we can add a destination NAT rule to redirect RDP to the client's PC.
	```bash
	/ip firewall nat add chain=dstnat protocol=tcp port=3389 in-interface=ether1 action=dst-nat to-address=192.168.88.254
	```
	*If you have set up strict firewall rules then RDP protocol must be allowed in the firewall filter forward chain.*

---
#### Setting up Wireless
The important part is to make sure that our wireless is protected, so the first step is the security profile.
```bash
/interface wireless security-profiles add name=myProfile authentication-types=wpa2-psk mode=dynamic-keys wpa2-pre-shared-key=1234567890
```

*If there are legacy devices that do not support WPA2 (like Windows XP), you may also want to allow WPA protocol.*

***WPA and WPA2 pre-shared keys should not be the same.***

![[winbox_wlan_sec_profile.png]]

Now when the security profile is ready we can enable the wireless interface and set the desired parameters:
```bash
/interface wireless enable wlan1
set wlan1 band=2ghz-b/g/n channel-width=20/40mhz-Ce distance=indoors mode=ap-bridge ssid=MikroTik-006360 wireless-protocol=802.11 security-profile=myProfile frequency-mode=regulatory-domain set country=latvia antenna-gain=3
```

![[winbox_wlan_iface.png]]

The last step is to add a wireless interface to a local bridge, otherwise connected clients will not get an IP address:
```bash
/interface bridge port add interface=wlan1 bridge=bridge1
```

---
#### Protecting the Clients
Now it is time to add some protection for clients on our LAN. We will start with a basic set of rules.
```bash
/ip firewall filter add chain=forward action=fasttrack-connection connection-state=established,related \ comment="fast-track for established,related"
add chain=forward action=accept connection-state=established,related comment="accept established,related"
add chain=forward action=drop connection-state=invalid add chain=forward action=drop connection-state=new connection-nat-state=!dstnat in-interface=ether1 comment="drop access to clients behind NAT from WAN"
```

A ruleset is similar to input chain rules (accept established/related and drop invalid), except the first rule with `action=fasttrack-connection`. This rule allows established and related connections to bypass the firewall and significantly reduce CPU usage.

Another difference is the last rule which drops all new connection attempts from the WAN port to our LAN network (unless DstNat is used). Without this rule, if an attacker knows or guesses your local subnet, he/she can establish connections directly to local hosts and cause a security threat.

---
#### Blocking Unwanted Websites
Sometimes you may want to block certain websites, for example, deny access to entertainment sites for employees, deny access to porn, and so on. This can be achieved by redirecting HTTP traffic to a proxy server and use an access-list to allow or deny certain websites.

First, we need to add a NAT rule to redirect HTTP to our proxy. We will use RouterOS built-in proxy server running on port 8080.
```bash
/ip firewall nat add chain=dst-nat protocol=tcp dst-port=80 src-address=192.168.88.0/24 action=redirect to-ports=8080
```

Enable web proxy and drop some websites:
```bash
/ip proxy set enabled=yes
/ip proxy access add dst-host=www.facebook.com action=deny
/ip proxy access add dst-host=*.youtube.* action=deny
/ip proxy access add dst-host=:vimeo action=deny`
```

---
## Notes
#### Troubleshoot if ping fails
![[troubleshoot_if_ping_fails.jpg]]




---
