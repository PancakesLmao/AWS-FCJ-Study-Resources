#services 

**AWS Transit Gateway** acts as a **central hub** that connects multiple **VPCs**, **on-premises networks**, and **VPNs** — enabling a **hub-and-spoke** network topology.

Instead of setting up multiple VPC peering connections, you can connect all your VPCs and networks to a single Transit Gateway, which simplifies routing and management.

# Features
| Feature                           | Description                                                           |
| --------------------------------- | --------------------------------------------------------------------- |
| **Managed Service**               | AWS provisions, manages, and scales it for you.                       |
| **Hub-and-Spoke Architecture**    | Connects thousands of VPCs and on-prem networks via a single gateway. |
| **Supports VPN & Direct Connect** | Integrates with Site-to-Site VPN and Direct Connect gateways.         |
| **Centralized Routing**           | Route traffic between VPCs and external networks using route tables.  |
| **Inter-Region Peering**          | Enables cross-region VPC-to-VPC communication.                        |
| **Multicast Support**             | Enables multicast traffic across VPCs for specific applications.      |
# Use Case
Imagine you have:
- 10 VPCs in the same region
- 1 VPN connection to your data center
Instead of setting up **45 VPC peering connections**, you attach all 10 VPCs and your VPN to a **Transit Gateway**, and it routes traffic intelligently between them
# Cost
- **Transit Gateway attachments** (per VPC/VPN/Direct Connect connection)
    - ~$0.05/hour per attachment
- **Data processing**
    - ~$0.02/GB of data processed through the TGW