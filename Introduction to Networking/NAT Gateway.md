#config #resources
 An **AWS NAT Gateway** (Network Address Translation Gateway) is a managed service that enables instances in a private subnet to connect to the internet or other AWS services, while preventing the internet from initiating connections with those instances.
# Types of NAT Gateway
## Public NAT Gateway
- **Location**: Deployed in a public subnet
- **Purpose**: Allows instances in private subnets to access the internet
- **Elastic IP**: Requires an associated Elastic IP address
- **Use Case**: When instances in private subnets need to access the internet for updates, patches, or external services

Public Subnet Route Table (NAT Gateway lives here):

| Destination | Target                              |
| ----------- | ----------------------------------- |
| `0.0.0.0/0` | **Internet Gateway (igw-xxxxxxxx)** |
Private Subnet Route Table (EC2 lives here):

| Destination | Target                         |
| ----------- | ------------------------------ |
| `0.0.0.0/0` | **NAT Gateway (nat-xxxxxxxx)** |

## Private NAT Gateway
- **Location**: Deployed in a private subnet.
- **Purpose**: Allows instances in private subnets to access other VPCs or on-premises networks via AWS Direct Connect or VPN
- **Elastic IP**: Does not require an Elastic IP address
- **Use Case**: When instances need to communicate with other networks without internet access.

Private Subnet A Route Table (Private NAT Gateway lives here):

| Destination                        | Target                             |
| ---------------------------------- | ---------------------------------- |
| On-prem CIDR (e.g., `10.1.0.0/16`) | **VPN Gateway / DX / VPC Peering** |
Private Subnet B Route Table (EC2 lives here):

|Destination|Target|
|---|---|
|On-prem CIDR (e.g., `10.1.0.0/16`)|**Private NAT Gateway**|
# How it work
**Outbound Traffic**: Instances in a private subnet send outbound traffic to the NAT Gateway.
**Address Translation**: The NAT Gateway translates the private IP addresses of the instances to its own public IP address.
**Internet Access**: The translated traffic is sent to the internet or other AWS services.
**Inbound Response**: Responses from the internet are received by the NAT Gateway, which then translates the destination address back to the private IP of the originating instance and forwards the response.
# Cost
AWS NAT Gateway pricing follows a **pay-as-you-go model**. You are charged **based on usage**, with **no upfront costs or long-term commitments**
- **Hourly Charges**: You are billed per hour for each NAT Gateway
- **Data Processing Charges**: You are billed per GB of data processed by the NAT Gateway