#services

Amazon Virtual Private Cloud (Amazon VPC) is a service that lets you create a private, customized network inside AWS. It acts like your own personal data center in the cloud, where you control the network settings.

# Route Tables

| Destination                                                               | Target                                                                                      |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| The range of IP addresses where you want traffic to go (destination CIDR) | The gateway, network interface, or connection through which to send the destination traffic |
E.g Routing a subnet to internet gateway

| Destination | Target                       |
| ----------- | ---------------------------- |
| 0.0.0.0/0   | igw-id (internet gateway id) |
| 10.0.0.0/16 | local                        |

With Amazon VPC, you can set up different sections (called subnets) in your network:
- **Public Subnet:** A section where resources like web servers can be accessed from the internet. This is useful for hosting websites and applications. Used to communicate between your instances and the internet
- **Private Subnet:** A section for backend systems like databases or internal servers. These do not have direct internet access, keeping them more secure.
--> Visit [[Subnets]] for more
In Amazon, VPC has the CIDR blocks between smallest /28 netmask and largest of /16 netmask (16 - 65536 IP Addresses)

***Subnets and Route Tables follow a many-to-one rule***
A subnet can be associated with only on route table at a time but you can associate many subnets to the same route table

To enhance security, Amazon VPC includes multiple protective layers:
- **[[Security Group]]s:** Act like firewalls that control what kind of traffic is allowed to and from specific resources (like EC2 instances).
- **[[Network ACL]]s (Access Control Lists):** Provide additional rules for controlling traffic at the subnet level.
## VPC ID and Tags
When you create a VPC, it will be auto-assigned a VPC ID. The VPC ID is a string of random numbers and letters that identify your VPC. This ID will be required when you associate additional components to your VPC, such as subnets and route tables. VPC IDs cannot be edited.
VPC ID example: vpc-0476e890abedg995f

Because the VPC ID can be difficult to remember, you have the option to tag your VPC with a more identifiable name. By tagging your VPC, the tag name appears after the VPC ID in parentheses when associating components to your VPC. You can tag every component of your VPC with an identifiable name, including subnets, route tables, and network access control lists (network ACLs). It is recommended that you tag these components to be sure that you are connecting the correct components together.
Compare how much simpler it can be to associate components to your VPC if they are tagged appropriately.

| Tagged VPC ID examples                   | Non-tagged VPC ID examples |
| ---------------------------------------- | -------------------------- |
| vpc-0476e890abedg995f (Development VPC)  | vpc-0476e890abedg995f      |
| vpc-s897fsf9afs09h3jk30 (Production VPC) | vpc-s897fsf9afs09h3jk30    |
| vpc-nj789sedjnalhalje30 (Testing VPC)    | vpc-nj789sedjnalhalje30    |

# What problem does VPC solved?
Amazon VPC provides features that you can use to increase and monitor the security for your virtual private cloud (VPC) **ON DEMAND**. Therefore, you can create a data center as you need it and terminate it when you no longer need it.

# Benefits
- Amazon VPC allows you to filter incoming and outgoing traffic at both the individual instance level (using security groups) and the subnet level (using network ACLs). This helps protect your resources from unauthorized access.
- Setting up Amazon VPC is straightforward, so you don’t have to spend too much time configuring it. This allows you to focus more on developing and running your applications rather than managing networking details.
- With Amazon VPC, you can customize your virtual network. You can: 
	Define your own **IP address range**
	Create and manage **subnets**
	Set up **route tables** to control how traffic moves within your network and to external gateways.

# Architect a Cloud solution using VPC
The diagram shows how you can use a VPC to build a solution that has both a public subnet and a private subnet. The public subnet has an EC2 instance that hosts a web application that has access to the internet. The private subnet has an RDS instance that is protected from direct access to the internet.
![Works with VPC](../attachments/works_with_VPC.png)

# How to use VPC
## Host a simple website
Use Amazon VPC to host a basic web application, such as a blog or simple website, you will gain the additional layers of privacy and security that the VPC configuration options provide
## Host multi-tier web applications
Use VPC to host multi-tier web application and strictly enforce access and security restrictions between your web servers, application servers, and databases. To achieve this result, you launch web servers in a publicly accessible subnet while running your application servers and databases in private subnets. This technique will ensure that application servers and databases cannot be directly accessed from the internet.
## Backup and recover
By using Amazon VPC for disaster recovery, you receive all the benefits of a disaster recovery site at a fraction of the cost. You can periodically back up critical data from your data center to as mall number of Amazon EC2 instances. Alternatively, you can import your virtual machine images to Amazon EC2. To ensure business continuity, you can use Amazon VPC to quickly launch replacement compute capacity in AWS. When the disaster is over, you can send your mission-critical data back to your data center.
## Extend your corporate network
You can use a VPC to move corporate applications to the cloud or launch additional web servers. You can also use a VPC to add more compute capacity to your network by connecting your VPC to your corporate network. Because your VPC can be hosted behind your corporate firewall, you can seamlessly move your IT resources into the cloud. You don't need to change how your users access these applications.

# What need to be kept in mind
When you create a new Amazon VPC, you have the option to create one by using a **template** or create one **from scratch**. When you create one from scratch, **automatically it will create a route table, a network ACL, and a security group**. Then, you configure them according to your needs. If you must delete a VPC, be sure to **first terminate** any EC2or RDS instances that you **have provisioned in the VPC**.

Each VPC is logically **isolated from other virtual networks in the AWS Cloud**, providing a secure foundation for workloads running on AWS.
**VPCs are region-specific resources,** meaning you can create **multiple VPCs** **within a SINGLE AWS Region**. Each VPC is identified by its unique IP address range (CIDR block), such as 10.0.0.0/16. **Once created, a VPC’s primary CIDR block cannot be changed.**
VPC CIDR blocks can range from:
- As large as /16 (65,536 IP addresses)
- As small as /28 (16 IP addresses)

***VPC CIDR blocks must not overlap with any other connected networks, including on-premises networks if you’re planning to connect them***

# VPC Architectural Patterns
## Single VPC Pattern
- 1 VPC per region/account
- All workloads live within that single VPC
- Private and public subnets managed in one place
Use cases:
- Small to medium workloads
- Startups, individual projects, or centralized management
## Multi-VPC Pattern
- Multiple VPCs in the same region/account
- Each VPC host a specific environment or team
- VPCs are connected using [[VPC Peering]] or [[AWS Transit Gateway]]
Use cases:
- Medium to large environments
- Separate environment (dev, staging, production)
- Need **better isolation and security**
## Multi-account VPC Pattern
- Each account has its own VPC(s)
- Accounts grouped into **OUs (Organizational Units)** (e.g., dev, security, networking)
- Centralized account may own **shared infrastructure** (like NAT, DNS, firewall)
Use cases:
- Large organizations, enterprise-scale
- Need **Separation of billing, security, compliance**
- Governance via AWS Organizations
# Cost
An Amazon VPC **doesn't cost you anything at a basic level**. In fact, when you set up your AWS account, you are given a default VPC. A VPC consists of many components that do not cost you anything, **such as subnets, route tables, network ACLs, security groups, and an internet gateway**. However, you can also add features to your Amazon VPC such as a **[[NAT Gateway]] and [[Elastic IP]]s that do have associated charges**. Also, any service that you place in your Amazon VPC, such as [[Amazon EC2]], will carry with it the associated cost for that service.