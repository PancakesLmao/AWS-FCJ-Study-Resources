#concepts
Open Systems Interconnection (OSI) Model is a suite of protocols or rules, to govern how computers communicate with one another
## Application Layer (Layer 7)
The application layer is the closest layer to the user, which means that both the OSI application layer and the user interact directly with the software application.
Application layer functions typically include identifying communication partners, determining resource availability, and synchronizing communication.
**Protocols: HTTP, HTTPS, FTP, SMTP, DNS, SNMP**
## Presentation Layer (Layer 6)
The presentation layer is responsible for formatting and delivering information to the application layer for further processing or display. It translates data based on the syntax that the application accepts (Data encryption/decryption, data compression, data translation).
Ex: Encrypting data before sending (like HTTPS with encryption with SSL/TLS)
## Session Layer (Layer 5)
The session layer provides the mechanism for opening, closing, and managing a session between user application processes.
Communication sessions consist of requests and responses that occur between applications (Establishing, maintaining and terminating sessions, synchronization, Dialog control).
Ex: Logging into a remote server via SSH or FTP—maintains session integrity
## Transport Layer (Layer 4)
The transport layer provides transparent transfer of data between users, and it provides reliable data transfer services to the upper layers. The transport layer controls the reliability of a given link through flow control, segmentation and desegmentation, and error control (Flow control).
Data Unit: Segment (TCP) / Datagrams (UDP)
This layer also provides the acknowledgement of the successful data transmission and sends the next data if no errors occurred (Error detection and correction, connection establishment and termination). 
**Protocol:** **TCP** (reliable), **UDP** (faster but no guarantee)
Ex: Watching a YouTube video (uses UDP for speed); logging into a bank (uses TCP for reliability).
## Network Layer (Layer 3)
The network layer is responsible for communication across different networks. It provides the means of transferring variable-length network packets from a source to a destination host through one or more networks (IP addressing like IPv4/IPv6, routing, packet forwarding, fragmentation and reassembly).
**Protocols: IP, ICMP, IGMP**
Devices: Router, Layer 3 Switches
Ex: Sending data from your PC in New York to a server in Germany.
## Data Link Layer (Layer 2)
The data link layer defines standards for transferring data between adjacent network nodes in a wide area network (WAN) or between nodes on the same local area network (LAN) segment.
This layer can provide the means to detect and possibly correct errors that might occur in the physical layer (MAC (Media Access Control) addressing, Error checking (CRC), Flow control, Frame synchronization).
Sub-layer: **MAC** (controls how devices on the same network gain access to data), **LLC** (provides interface between the network layer and MAC)
Devices: Switches, network interface cards (NICs)
Ex: Ethernet addressing (MAC address communication)
## Physical Layer (Layer 1)
The physical layer defines standards for transmitting raw data (bits) over transmission media to connect network nodes. The physical layer provides an electrical, mechanical, and procedural interface to the transmission medium.
**Data Unit: Bits (0s and 1s)**
Devices: Hubs, repeaters, network cables
Ex: The Ethernet cable that connects your computer to a router

# Summary

|Layer|Name|Data Unit|Example Protocols/Devices|
|---|---|---|---|
|7|Application|Data|HTTP, FTP, SMTP, DNS|
|6|Presentation|Data|SSL, TLS, JPEG, ASCII|
|5|Session|Data|NetBIOS, RPC, PPTP|
|4|Transport|Segments|TCP, UDP|
|3|Network|Packets|IP, ICMP, IGMP|
|2|Data Link|Frames|Ethernet, MAC, Switches|
|1|Physical|Bits|Cables, Hubs, NICs, Wi-Fi
