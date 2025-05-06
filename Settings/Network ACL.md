#config
A NACL is an optional layer of security for your VPC that acts as a **stateless firewall** for controlling traffic in and out of one or more **subnets**.
A NACL provides fine-grained control of traffic at the subnet level, complementing security groups, which operate at the instance level. NACLs are especially useful when you want to implement **broad traffic filtering rules** across multiple instances in a subnet.
# Rule Features
- Controls **inbound and outbound traffic** at the **subnet level**
- **Supports both allow and deny rules**
- **Stateless**: return traffic must be explicitly allowed
- Rules are **evaluated in order**, starting from the **lowest number**
# Rule Components
## Rule number
Each rule is associated with a rule number from **1–32766**. AWS evaluates rules in order, starting from the lowest number. The first match determines whether to allow or deny traffic.
## Protocol
Specifies the protocol that the rule applies to. You can use:
- `6` for TCP
- `17` for UDP
- `1` for ICMP
- `-1` for **all protocols**
## Port range
Defines the allowed or denied range of ports for the rule, similar to security groups. You can specify a single port (e.g., `80`) or a range (`1000-2000`)
**Ephemeral ports** are **temporary ports** assigned by the client's operating system when it initiates an **outbound** connection (`32768–65535`). If your **NACL** or **firewall** blocks ephemeral ports, return traffic may be dropped, breaking your connection
E.g:

|EC2 Role|NACL Inbound Rule Needed|NACL Outbound Rule Needed|
|---|---|---|
|**Client**|Ephemeral ports (32768–65535) ✅|HTTP/HTTPS (80/443) ✅|
|**Server**|HTTP/HTTPS (80/443) ✅|Ephemeral ports ✅ (for response)|
## Source/Destination
Specifies the IP address range the rule applies to:
- **Inbound rules**: source IP
- **Outbound rules**: destination IP
## Allow/Deny
Unlike security groups, NACLs explicitly support **both ALLOW and DENY** rules. This gives you more control but requires careful management to avoid unintended blocking.
# Inbound and Outbound Rules

## Inbound rule
Controls incoming traffic **into the subnet**. Each rule must specify source, protocol, port range, and allow/deny action.
## Outbound rule
Controls outgoing traffic **from the subnet** to other destinations. Must specify destination, protocol, port range, and allow/deny action.
If **no rule matches**, the default is to **deny** traffic.
# STATELESS Attributes

NACLs are **stateless**: responses to allowed inbound traffic **must be explicitly allowed** in outbound rules, and vice versa.
No automatic return traffic allowance like in security groups.

|Inbound Rule|Outbound Rule|Traffic Behavior|
|---|---|---|
|Allow HTTP|No rule|Response blocked|
|Allow HTTP|Allow HTTP|Bidirectional OK|
# Managing Network ACLs
- NACLs act at the **SUBNET LEVEL**, not the instance level.
- Each subnet in your VPC **must be associated** with a NACL (default NACL allows all traffic).
- A single NACL can be associated with **multiple subnets** (but a subnet can have only **one NACL**).
- Use **NACLs for broad filtering**, like blocking IP ranges across multiple instances.
- Changes to NACLs are applied **immediately**
