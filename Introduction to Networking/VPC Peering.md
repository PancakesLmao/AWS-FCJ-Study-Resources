**VPC Peering** enables you to route traffic **privately** between two VPCs as if they were part of the same network. It's useful for secure and low-latency communication between VPCs **without needing VPNs, NAT Gateways, or public internet.**

# Characteristics
| Feature                        | Description                                                                            |
| ------------------------------ | -------------------------------------------------------------------------------------- |
| **One-to-one connection**      | Peering is set up between two VPCs. Not transitive — you must peer each pair manually. |
| **No single point of failure** | It uses AWS's internal backbone — highly reliable.                                     |
| **Secure**                     | No traffic goes over the internet.                                                     |
| **Supports cross-account**     | You can peer VPCs from different AWS accounts.                                         |
| **Cross-region support**       | Available globally (some restrictions may apply per region).                           |
|                                |                                                                                        |
## Restrictions
- **No transitive routing**  
    If VPC A is peered with B, and B with C — A **cannot** reach C via B.
- **IP address overlap not allowed**  
    Peered VPCs must have **non-overlapping CIDR blocks**.
- **Manual scaling**  
    As the number of VPCs grows, managing many peerings becomes complex. For that, consider **Transit Gateway**.
# Use Cases
- Microservices in separate VPCs (e.g., dev/staging/prod).
- Cross-account access (e.g., security VPC, logging VPC).
- Multi-region communication (e.g., backup replication).

Configuration example
For two peered VPCs:
- **VPC A**: 10.0.0.0/16
- **VPC B**: 192.168.0.0/16

You add this route in VPC A's route table:

|Destination|Target|
|---|---|
|192.168.0.0/16|Peering Connection ID (pcx-xxxxxx)|

And the reverse in VPC B:

|Destination|Target|
|---|---|
|10.0.0.0/16|Peering Connection ID (pcx-xxxxxx)|
# Cost
- **VPC Peering itself is free** (no hourly charge).
- You **pay for data transfer**:
    - **Same region**: standard EC2 rates (e.g., $0.01/GB)
    - **Cross-region**: more expensive (e.g., ~$0.02/GB)
***Still cheaper than using NAT + Internet Gateway for internal traffic.***