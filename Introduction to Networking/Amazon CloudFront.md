#services 

**Amazon CloudFront** is a **global content delivery network (CDN)** that securely delivers data, videos, applications, and APIs to users with low latency and high transfer speeds.

# Features
| Feature                        | Description                                                                                                |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------- |
| **Global Edge Network**        | 700+ PoPs + 900+ embedded locations; automatic routing & intelligent path selection                        |
| **Caching**                    | Multi-layer caching (edge + 13 Regional Edge Caches + Origin Shield)                                       |
| **Origin Shield**              | Optional centralized caching layer – dramatically reduces origin load and improves hit ratios              |
| **Origin Support**             | S3, EC2, ALB, API Gateway, Elemental Media Services, custom HTTP/S origins, on-premises servers            |
| **Origin Failover**            | Native automatic failover to secondary origin (now included in Business/Premium/Custom plans)              |
| **HTTPS/TLS**                  | TLS 1.3, free ACM certificates, OCSP stapling, Session Tickets, Perfect Forward Secrecy                    |
| **Security**                   | AWS Shield Standard (free), AWS WAF, geo-restriction, signed URLs/cookies, Field-Level Encryption, OAC/OAI |
| **Programmability**            | CloudFront Functions (sub-ms lightweight JS) + Lambda@Edge (full Node.js/Python compute)                   |
| **Real-Time Logs & Metrics**   | CloudWatch metrics, standard S3 logs, real-time logs to Kinesis Data Streams                               |
| **Continuous Deployment**      | Built-in blue/green, weighted routing, session stickiness, instant rollback support                        |
| **Compression & Optimization** | Brotli + Gzip, automatic image optimization (via Lambda@Edge or partner solutions)                         |
## Security and Compliance

- HTTPS/TLS everywhere with free ACM certificates (global)
- Origin Access Control (OAC) – preferred way to lock S3/custom origins
- AWS Shield Standard (always free) + Shield Advanced (in higher plans)
- AWS WAF with managed rules, rate limiting, bot control (rules & sophistication scale with plan)
- Signed URLs & Signed Cookies (time-limited private content)
- Geo-restriction & geo-blocking
- Field-Level Encryption (encrypt specific fields before they reach your origin)
## Integration with AWS
|AWS Service|CloudFront Role|
|---|---|
|S3|Primary static content origin + OAC for private buckets|
|EC2 / ALB / API Gateway|Dynamic content & API acceleration|
|Elemental Media Services|Live & on-demand video streaming|
|Lambda@Edge / CloudFront Functions|Edge compute & content personalization|
|AWS WAF & Shield|Layer 7 protection & DDoS mitigation (bundled in all plans)|
|Certificate Manager (ACM)|Free public certificates (now global, not just us-east-1)|
|Route 53|DNS + health checks (included in all flat-rate plans)|
|CloudWatch / Kinesis|Metrics & real-time logging|
|Origin Shield|Extra caching layer to protect any origin|

# Use Cases
- Static website & asset delivery (S3 + CloudFront)
- Global API acceleration (API Gateway / ALB)
- Video streaming (live & VOD)
- Software downloads & OTA updates
- Dynamic personalization & A/B testing at the edge
- Security-sensitive applications (private content, bot mitigation, WAF)
# What need to be keep in mind
|Aspect|Detail|
|---|---|
|**Plan Selection**|Free → Pro → Business → Premium. You can mix plans across different distributions.|
|**Usage Allowances**|Exceeding requests/data transfer in a plan = throttling (not overage charges). Upgrade to remove.|
|**Invalidations**|Still pay-as-you-go (first 1 000 paths free/month, then $0.005 each) – not included in flat plans.|
|**Lambda@Edge / Functions**|Included in all plans, but heavy Lambda@Edge usage still has separate compute charges.|
|**Logging Volume**|Real-time logs to Kinesis can generate huge volume → cost & retention planning needed.|
|**Origin Shield**|Free to enable, but dramatically reduces origin egress costs.|
|**Cold Cache**|First request still goes to origin; use Cache Warmers or Origin Shield for large objects.|
|**Custom SSL via ACM**|Now free in all regions (no more us-east-1 limitation).|
# Cost
Updated to **Flat Pricing** on 19th November 2025
CloudFront flat-rate pricing plans combine the Amazon CloudFront global content delivery network (CDN) with multiple AWS services and features into a monthly price with **no overage charges**.

Flat-rate pricing plans include the following for a monthly price:  
• CloudFront CDN  
• AWS WAF and DDoS protection  
• Bot management and analytics  
• Amazon Route 53 DNS  
• Amazon CloudWatch Logs ingestion  
• TLS certificate  
• Serverless edge compute  
• Amazon S3 storage credits each month

Start with the $0/month Free plan and upgrade to access more capabilities and larger usage allowances.

# Reference
[CLoudFront Pricing](https://aws.amazon.com/cloudfront/pricing/)