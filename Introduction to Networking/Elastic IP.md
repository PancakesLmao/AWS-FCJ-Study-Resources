An **Elastic IP (EIP)** in AWS is a **static, public IPv4 address** that you can allocate to your AWS account and **associate with EC2 instances or network interfaces**.
# What is an Elastic IP?
- A **static public IP address** designed for dynamic cloud computing
- You can **associate and re-associate** it with different EC2 instances in your account
- Remains yours **until you release it**, even if the associated instance is stopped or terminated

***AWS encourages the use of Auto Scaling + Load Balancers instead of relying heavily on EIPs***

# Pricing
| Scenario                                                   | Price (per hour)            |
| ---------------------------------------------------------- | --------------------------- |
| **1. First EIP associated with a running instance**        | **Free**                    |
| **2. Unused EIP (not associated with a running instance)** | ~$0.005/hour (≈$3.60/month) |
| **3. Additional EIPs (per instance, beyond the first)**    | ~$0.005/hour each           |
### Best Practices to Avoid Charges
- **Release** unused Elastic IPs.
- Use **Elastic Load Balancers** or **Route 53** for scalability instead of multiple EIPs.
- Stick to **one EIP per instance** when absolutely needed.