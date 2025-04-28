**Internet Protocol** is the set of rules that governs how data is sent from one computer to another across the internet. It is a **connectionless protocol**, meaning it sends packets (chunks of data) without establishing a connection beforehand.
IP is part of the **[[OSI Model#Network Layer (Layer 3)]]** in the OSI model.
# IP Addresses
An **IP address** is a **unique identifier** for a device on a network.
It acts like a **home address**, helping route data to the correct destination.
# IPv4 and IPv6
## IPv4
**Most widely used** version of IP, has:
- **32-bit** address (4 bytes)
- Written in **dotted decimal** (`192.168.0.1`)
Let's break it down: 
- 32 bits = 4 octets (8 bits each)
- Range: `0.0.0.0` to `255.255.255.255`
- Total unique addresses: **~4.3 billion**
Ex: we have `192.168.10.15` as `11000000.10101000.00001010.00001111` in binary format
## IPv6
Created due to IPv4 exhaustion, has:
- **128-bit** address
- Written in **hexadecimal** and colon-separated (`2001:0db8:85a3:0000:0000:8a2e:0370:7334`)
Let's break it down"
- 8 groups of 4 hex digits (16 bits per group)
- Uses `::` to compress consecutive zeros
- Virtually **unlimited addresses** (~3.4×10³⁸)
Advantages over IPv4: 
- **No need for NAT** (Network Address Translation)
- Built-in security (IPSec)
- More efficient routing and packet handling

| Feature         | IPv4                         | IPv6                             |
| --------------- | ---------------------------- | -------------------------------- |
| Address Size    | 32-bit                       | 128-bit                          |
| Format          | Decimal, e.g., `192.168.1.1` | Hexadecimal, e.g., `2001:db8::1` |
| Total Addresses | ~4.3 billion                 | ~3.4×10³⁸                        |
| CIDR Support    | Yes                          | Yes                              |
| NAT Required    | Often                        | Not usually                      |
| Security        | Optional (IPSec)             | Built-in (mandatory)             |

# Classes Inter-Domain Routing (CIDR)
CIDR is a **notation method** used to denote **IP address ranges** more efficiently than older class-based systems.
`{IP Address} / {Prefix Length}`
Ex: `192.168.1.0/24`
`/24` means the **first 24 bits** are the **network portion**, so the range is: 
`192.168.1.0` to `192.168.1.255` (256 IPs)
## CIDR Prefix Chart (Common Ones):
| CIDR | Subnet Mask     | Number of IPs | Use Case             |
| ---- | --------------- | ------------- | -------------------- |
| /8   | 255.0.0.0       | 16,777,216    | Huge networks        |
| /16  | 255.255.0.0     | 65,536        | Medium networks      |
| /24  | 255.255.255.0   | 256           | Small LANs           |
| /30  | 255.255.255.252 | 4             | Point-to-point links |
## Special cases
### Fixed IP Address
All 32-bit are fixed
`192.168.2.0/32`
Use case: Set up firewall rule and give access to a specific host 
### Internet CIDR Block 
All 32-bits are flexible
`0.0.0.0/0`
Use case: Set up firewall rules to allow internet traffic 
## Full version
|CIDR|Subnet Mask|Usable Hosts|Total IPs|Example Range (192.168.0.0/x)|
|---|---|---|---|---|
|/32|255.255.255.255|0|1|192.168.0.0 (single IP)|
|/31|255.255.255.254|0|2|192.168.0.0 - 192.168.0.1 (point-to-point)|
|/30|255.255.255.252|2|4|192.168.0.0 - 192.168.0.3|
|/29|255.255.255.248|6|8|192.168.0.0 - 192.168.0.7|
|/28|255.255.255.240|14|16|192.168.0.0 - 192.168.0.15|
|/27|255.255.255.224|30|32|192.168.0.0 - 192.168.0.31|
|/26|255.255.255.192|62|64|192.168.0.0 - 192.168.0.63|
|/25|255.255.255.128|126|128|192.168.0.0 - 192.168.0.127|
|/24|255.255.255.0|254|256|192.168.0.0 - 192.168.0.255|
|/23|255.255.254.0|510|512|192.168.0.0 - 192.168.1.255|
|/22|255.255.252.0|1022|1024|192.168.0.0 - 192.168.3.255|
|/21|255.255.248.0|2046|2048|192.168.0.0 - 192.168.7.255|
|/20|255.255.240.0|4094|4096|192.168.0.0 - 192.168.15.255|
|/19|255.255.224.0|8190|8192|192.168.0.0 - 192.168.31.255|
|/18|255.255.192.0|16,382|16,384|192.168.0.0 - 192.168.63.255|
|/17|255.255.128.0|32,766|32,768|192.168.0.0 - 192.168.127.255|
|/16|255.255.0.0|65,534|65,536|192.168.0.0 - 192.168.255.255|
|/15|255.254.0.0|131,070|131,072|192.168.0.0 - 192.169.255.255|
|/14|255.252.0.0|262,142|262,144|192.168.0.0 - 192.171.255.255|
|/13|255.248.0.0|524,286|524,288|192.168.0.0 - 192.175.255.255|
|/12|255.240.0.0|1,048,574|1,048,576|192.168.0.0 - 192.183.255.255|
|/11|255.224.0.0|2,097,150|2,097,152|192.168.0.0 - 192.191.255.255|
|/10|255.192.0.0|4,194,302|4,194,304|192.168.0.0 - 192.207.255.255|
|/9|255.128.0.0|8,388,606|8,388,608|192.168.0.0 - 192.255.255.255|
|/8|255.0.0.0|16,777,214|16,777,216|192.0.0.0 - 192.255.255.255|