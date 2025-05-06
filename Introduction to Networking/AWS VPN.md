#services 
**AWS VPN** allows you to securely connect your on-premises network or client devices to your Amazon VPC over an encrypted IPsec VPN tunnel across the internet.

# Types of AWS VPN
## Site-to-Site VPN
- **Purpose**: Connects an on-premises network (like a data center) to an AWS VPC.
- **Tunnels**: Two IPsec VPN tunnels for redundancy.
- **Attachment**: Typically connected to a **Virtual Private Gateway (VGW)** or **Transit Gateway**.
- **Use Case**: Hybrid cloud setups.
## Client VPN
- **Purpose**: Allows remote users (e.g., developers, employees) to connect securely to AWS resources.
- **Based on**: OpenVPN.
- **Use Case**: Secure remote access.

# Components
| Component                         | Description                                                    |
| --------------------------------- | -------------------------------------------------------------- |
| **VGW (Virtual Private Gateway)** | AWS side of the VPN connection attached to a VPC.              |
| **Customer Gateway (CGW)**        | Your on-premises device or software that initiates the tunnel. |
| **Transit Gateway (TGW)**         | Optional – central hub for multiple VPCs and on-prem networks. |
| **VPN Connection**                | The actual IPsec connection between CGW and VGW/TGW.           |
# Cost
- **0.05/hour per VPN connection**.
- **Outbound data transfer** incurs standard AWS egress charges.
- No charge for inbound data.
## Best Practices
- Use **both tunnels** for high availability.
- Monitor health via **CloudWatch metrics**.
- Use **BGP** for automatic failover if possible.
- For multi-VPC connectivity, prefer **Transit Gateway** + VPN over multiple VGW links.
- Use **Client VPN** with MFA and IAM-based authentication for user access.