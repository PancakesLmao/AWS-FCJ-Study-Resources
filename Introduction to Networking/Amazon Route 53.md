#services 

**Amazon Route 53** is a **DNS and traffic routing service** that connects user requests to applications hosted on AWS or externally. It is named after port **53**, the port DNS uses.

# Features
| Feature                                 | Description                                                                |
| --------------------------------------- | -------------------------------------------------------------------------- |
| **Domain Registration**                 | Register and manage domain names directly within Route 53.                 |
| **DNS Service**                         | Authoritative DNS that translates domain names into IP addresses.          |
| **Health Checks**                       | Monitor the health of endpoints (EC2, ELB, on-prem) and route accordingly. |
| **Traffic Flow (Geo/Routing Policies)** | Route traffic based on latency, location, or weighted values.              |
| **Private DNS (for VPC)**               | Create private hosted zones for use inside VPCs.                           |
| **DNS Failover**                        | Automatically failover traffic to healthy resources.                       |
| **Routing Policies**                    | Multiple routing strategies supported (see below).                         |
# Policy Types
| Policy Type           | Description                                                 |
| --------------------- | ----------------------------------------------------------- |
| **Simple**            | One IP or resource per DNS name (basic).                    |
| **Weighted**          | Split traffic based on percentages.                         |
| **Latency-based**     | Route to the region with the lowest latency.                |
| **Geolocation**       | Route based on user’s location.                             |
| **Geo-proximity**     | Route based on geographic distance (requires Traffic Flow). |
| **Failover**          | Route to backup when primary is unhealthy.                  |
| **Multivalue Answer** | Returns multiple IPs, adds health check-like behavior.      |
# Use Cases
- Domain registration + DNS for websites and APIs.
- Load balancing across AWS and on-prem servers.
- Failover to backup resources if primary fails.
- Geo-based content delivery.
- Hybrid and multi-region DNS setup.
# Integration with Other AWS Services

|Service|Role with Route 53|
|---|---|
|**Elastic Load Balancer (ELB)**|Use as DNS target for routing traffic.|
|**CloudFront**|Route domain traffic to CDN distribution.|
|**S3 Static Websites**|Route to static web hosting.|
|**API Gateway**|Route to custom domain APIs.|
|**VPC (Private Hosted Zone)**|Custom DNS resolution inside VPC.|
|**Health Checks**|Works with EC2, ELB, or any IP target.|
# Common Architectures

- Route 53 → CloudFront → ALB → EC2 instances
- Route 53 → S3 static website
- Route 53 with failover between on-prem and AWS
- Multi-region latency-based routing
# What need to be keep in mind
| Consideration            | Description                                                                   |
| ------------------------ | ----------------------------------------------------------------------------- |
| **DNS Propagation Time** | TTL affects how quickly changes take effect.                                  |
| **No zone-level DNSSEC** | DNSSEC support is only for domain registration, not hosted zones (as of now). |
| **Failover Cost**        | Health checks add to monthly costs.                                           |
| **Complex Routing**      | Some routing policies require Traffic Flow or special configuration.          |
# Cost 
| Feature                   | Pricing (as of May 2025)             |
| ------------------------- | ------------------------------------ |
| **Hosted Zone**           | $0.50/month per hosted zone          |
| **DNS Queries**           | $0.40–$0.60/million queries          |
| **Health Checks**         | ~$0.50/month per check               |
| **Domain Registration**   | Varies by TLD (e.g., .com ~$12/year) |
| **Traffic Flow Policies** | Additional charges may apply         |