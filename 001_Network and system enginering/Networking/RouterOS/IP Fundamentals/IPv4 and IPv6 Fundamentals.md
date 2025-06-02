---
Category: Main Chapter
tags:
  - mainChapter
  - open
---
---
###### External links

---
## Table of contents
- [[ARP]]
- [[001_Network and system enginering/Networking/RouterOS/IP Fundamentals/TCP IP|TCP IP]]
- [[IPv4 Adressing]]
- [[IPv6 Adressing]]
- 

- ### Chapters
	- 

---
## Core information
### Networking Models
#### OSI Model
The Open Systems Interconnection (OSI) model is a 7-layer model that today is used as a teaching tool. The OSI model was originally conceived as a standard architecture for building network systems, but in real-world networks are much less defined than the OSI model suggests.

- **Layer 7 (Application)** - a protocol that defines the communication between the server and the client, for example, HTTP protocol. If the web browser wants to download an image, the protocol will organize and execute the request;
- **Layer 6 (Presentation)** - ensures data is received in a usable format. Encryption is done here (but in reality it may not be true, for example, IPSec);
- **Layer 5 (Session)** - responsible for setting up, managing and closing sessions between client and server;
- **Layer 4 (Transport)** - transport layers primary responsibility is assembly and reassembly, a data stream is divided into chunks (segments), assigned sequence numbers and encapsulated into protocol header (TCP, UDP, etc.);
- **Layer 3 (Network)** - responsible for logical device addressing, data is encapsulated within an IP header and now called "packet";
- **Layer 2 (Data link)** - Data is encapsulated within a custom header, either 802.3 (Ethernet) or 802.11 (wireless) and is called "frame", handles flow control;
- **Layer 1 (Physical)** - Communication media that sends and receives bits, electric signaling, and hardware interface;

#### TCP/IP Model
This model has the same purpose as the OSI model but fits better into modern network troubleshooting. Comparing to the OSI model, TCP/IP is a 4-layer model:

- **Application layer (4)** - includes application, presentation and session layers of the OSI model, which significantly simplifies network troubleshooting;
- **Transport layer (3)** - same as a transport layer in the OSI model (TCP, UDP protocols);
- **Internet layer (2)** - does the same as Network layer in the OSI model (include ARP, IP protocols);
- **Link layer (1)** - also called the Network Access layer. Includes both Layer1 and 2 of the OSI model, therefore its primary concern is physical data exchange between network nodes;

| TCP/IP            | OSI Model          | Protocols                       |
| ----------------- | ------------------ | ------------------------------- |
| Application Layer | Application Layer  | DNS, DHCP,HTTP,SSH etc.         |
|                   | Presentation Layer | JPEG,MPEG,PICT etc.             |
|                   | Session Layer      | PAP, SCP, ZIP etc.              |
| Transport Layer   | Transport Layer    | TCP, UDP                        |
| Internet Layer    | Network Layer      | ICMP, IGMP, IPv4, IPv6, IPSec   |
| Link Layer        | Data Link Layer    | ARP, CDP, MPLS, PPP etc.        |
|                   | Physical Layer     | Bluetooth, Ethernet, Wi-Fi etc. |

---
### Ethernet
Ну понятное дело шо линк леер протокол, использует (Media Access Control address) или эзернет адрес из 6 по 8 бит.

`/interface ethernet> print`

Есть 3 типа эзернет адреса:
- юникаст
- бродкаст (`FF:FF:FF:FF:FF:FF`)
- мультикаст
---
### IP Networking
Понятное дело шо протокол эзернет не может сам по себе работать. И шоб определить уникальных хостов в сети или интернете - юзается Internet Protocol.
Понятно, шо адрес 4 октета - 32 бита, ну и для различия сети и хоста используется маска, которая делит на адрес сети и на юникаст адрес хоста.

- Широковещание (бродкаст) - отсылает даные один раз всем хостам. Для локального широковещания используется адрес 255.255.255.255. Ну и ограниченное широковещание может быть направлено на широковещательный адрес локальной сети.

- мультикаст (багатоадресна розсилка) - маршрутизаторы пересылают всем, кто подтянулся до групы многоадресной рассылки. В IPv4 это адреса `224.0.0.0` по `239.255.255.255`.

#### Private address range
- `10.0.0.0/8` - start: `10.0.0.0`; end: `10.255.255.255`
- `172.16.0.0/12` - start: `172.16.0.0`; end:`172.31.255.255`
- `192.168.0.0/16` - start: `192.168.0.0`; end: `192.168.255.255`

---


