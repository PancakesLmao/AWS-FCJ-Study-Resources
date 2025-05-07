#services 

**Amazon CloudFront** is a **global content delivery network (CDN)** that securely delivers data, videos, applications, and APIs to users with low latency and high transfer speeds.

# Features
| Feature                 | Description                                                                  |
| ----------------------- | ---------------------------------------------------------------------------- |
| **Global Edge Network** | 400+ edge locations worldwide to cache and serve content near users.         |
| **Caching**             | Reduces load on origin by storing responses at edge locations.               |
| **Origin Support**      | Works with S3, EC2, ALB, API Gateway, Media Services, on-prem servers, etc.  |
| **HTTPS/SSL Support**   | Full SSL/TLS encryption with custom or AWS-managed certificates.             |
| **Security**            | Integrates with AWS Shield, WAF, and IAM. Supports signed URLs/cookies.      |
| **Real-Time Logs**      | Supports CloudWatch, S3 logs, and Kinesis Data Streams for traffic insights. |
| **Lambda@Edge**         | Run serverless functions at edge locations to customize content and headers. |
| **Origin Failover**     | Automatically failover to a secondary origin if the primary is unavailable.  |
## Security and Compliance

- **HTTPS everywhere** with custom SSL certificates via ACM.
- **Origin Access Control (OAC)**: Restrict access to S3 or origin only via CloudFront.
- **Signed URLs/Cookies** for secure, time-limited access.
- **WAF & AWS Shield** integration for DDoS and Layer 7 attack protection.
- **Geo restriction**: Block or allow access based on geographic location.
## Integration with AWS

| AWS Service                   | CloudFront Role                           |
| ----------------------------- | ----------------------------------------- |
| **S3**                        | Distribute static content with caching.   |
| **API Gateway**               | Distribute APIs with global acceleration. |
| **Lambda@Edge**               | Customize requests/responses globally.    |
| **Shield/WAF**                | Security layer against threats.           |
| **Certificate Manager (ACM)** | Attach free public SSL certs.             |
| **Route 53**                  | Use custom domains with CloudFront.       |
# Use Cases
| Feature                 | Description                                                                  |
| ----------------------- | ---------------------------------------------------------------------------- |
| **Global Edge Network** | 400+ edge locations worldwide to cache and serve content near users.         |
| **Caching**             | Reduces load on origin by storing responses at edge locations.               |
| **Origin Support**      | Works with S3, EC2, ALB, API Gateway, Media Services, on-prem servers, etc.  |
| **HTTPS/SSL Support**   | Full SSL/TLS encryption with custom or AWS-managed certificates.             |
| **Security**            | Integrates with AWS Shield, WAF, and IAM. Supports signed URLs/cookies.      |
| **Real-Time Logs**      | Supports CloudWatch, S3 logs, and Kinesis Data Streams for traffic insights. |
| **Lambda@Edge**         | Run serverless functions at edge locations to customize content and headers. |
| **Origin Failover**     | Automatically failover to a secondary origin if the primary is unavailable.  |
# What need to be keep in mind
| Aspect                      | Detail                                                 |
| --------------------------- | ------------------------------------------------------ |
| **Latency-sensitive setup** | Use Lambda@Edge wisely to avoid delays.                |
| **Cold cache**              | Initial requests may go to origin and incur more cost. |
| **Invalidation cost**       | Frequent content changes may increase cost.            |
| **Custom SSL Certs**        | Free via ACM only in US/EU regions.                    |
| **Logging volume**          | Logs can be large and impact S3 costs.                 |
# Cost
It follows pay-as-you-go model

| Item                              | Typical Cost (May 2025)                        |
| --------------------------------- | ---------------------------------------------- |
| **Data Transfer Out to Internet** | $0.085–$0.20/GB (depends on region and volume) |
| **Requests (per 10,000)**         | ~$0.0075 for HTTP, ~$0.01 for HTTPS            |
| **Invalidation Requests**         | First 1,000/month free, then ~$0.005/request   |
| **Field-level Encryption**        | ~$0.02 per 10,000 requests                     |
| **Lambda@Edge Invocations**       | ~$0.60/million + execution time                |