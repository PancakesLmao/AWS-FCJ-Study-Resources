A **subnet** (short for **subnetwork**) is a **smaller, logical section** of a larger network. Subnetting divides a big IP network into multiple **smaller, manageable networks**.
# Subnet CIDR Block
Suppose your company has a `192.168.10.0/24` network and you need **4 subnets**. You can do:
Divide into 4 Subnets (use /26):
- New CIDR: `/26` (you borrow 2 bits)
- Each subnet = 64 IPs (62 usable)

|Subnet #|Network Address|Range|Broadcast Address|
|---|---|---|---|
|Subnet 1|192.168.10.0/26|192.168.10.1–62|192.168.10.63|
|Subnet 2|192.168.10.64/26|192.168.10.65–126|192.168.10.127|
|Subnet 3|192.168.10.128/26|192.168.10.129–190|192.168.10.191|
|Subnet 4|192.168.10.192/26|192.168.10.193–254|192.168.10.255|
# Subnet Types
## Public subnets
A public subnet **allows internet traffic** that is **routed through an [[Internet gateway]] (IGW)** to reach the subnet. A public subnet might make a good choice if you have a website that is targeting customers.
## Private subnets
A private subnet **denies traffic to the subnet that is routed from the public internet**. You should use a private subnet if your network must connect to services outside your network but must **restrict external services** from initializing connection to your network. **Access to the public internet from a private subnet requires a NAT device. [[NAT Gateway]]**
## [[Virtual Private Gateway]]

# Subnetting in AWS
For **each subnet CIDR block** that you specify, AWS reserves five IP addresses within that block, and
these addresses are not available for use.

| Reserved IP address for AWS CIDR blocks   | Purpose of reservation                    |
| ---------------------------------------- | ----------------------------------------- |
| 1st                                       | Network address                           |
| 2nd                                       | VPC local router (internal communication) |
| 3r                                   P    | Domain name system (DNS) resolution       |
| 4                                   IP    | Future use                                |
| L                                  t IP   | Network broadcast address                 |
