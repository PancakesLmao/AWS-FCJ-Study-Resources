#services 

**Amazon API Gateway** is a **fully managed service** that makes it easy for developers to create, publish, maintain, monitor, and secure **RESTful, HTTP, and WebSocket APIs** at any scale.

# Features
|Feature|Description|
|---|---|
|**REST APIs**|Fully featured APIs with support for transformations, validation, and throttling.|
|**HTTP APIs**|Lighter-weight, faster, and cheaper for proxy use cases.|
|**WebSocket APIs**|Real-time bi-directional communication (e.g. chat, gaming).|
|**Lambda Integration**|Serverless backend using AWS Lambda.|
|**Private APIs**|Accessible only within your VPC.|
|**Custom Domain Support**|Use your own domain name for the API.|
|**Rate Limiting & Throttling**|Protect backend services from overuse.|
|**Authorization**|Supports IAM, Cognito, Lambda authorizers, and API keys.|
|**Caching**|Built-in cache to reduce backend load and latency.|
|**Monitoring**|CloudWatch integration for metrics and logging.|
# API Types
|Type|Use Case|
|---|---|
|**REST API**|Feature-rich APIs with request/response transformations.|
|**HTTP API**|Lightweight, faster and more cost-effective. Best for proxying to Lambda/HTTP endpoints.|
|**WebSocket API**|Real-time apps (chats, live dashboards, multiplayer games).|
## Security

| Security Layer             | Details                                                                 |
| -------------------------- | ----------------------------------------------------------------------- |
| **IAM Permissions**        | Restrict access using AWS IAM roles and policies.                       |
| **Cognito Authorizers**    | Use user pools for identity and access management.                      |
| **Lambda Authorizers**     | Custom logic for authentication and authorization.                      |
| **API Keys & Usage Plans** | Rate-limit and track API usage.                                         |
| **Private APIs**           | Restrict access to within your VPC via interface endpoints (VPC Links). |
| **TLS (HTTPS)**            | All API Gateway endpoints use HTTPS.                                    |
# Backend Integrations

- **AWS Lambda**
- **Amazon EC2 / ALB / ECS**
- **Any public HTTP endpoint**
- **AWS services via AWS service integrations** (e.g., S3, DynamoDB)

# Use Cases

- Build **serverless APIs** with Lambda.
- Proxy requests to **EC2, containers, or third-party services**.
- Create real-time applications (WebSocket).
- Expose AWS services like **DynamoDB or S3** via secure APIs.
- Secure microservices and enforce throttling/quotas.
- Build **multi-tenant APIs** using custom authorizers.
# What need to be keep in mind
|Concern|Description|
|---|---|
|**Cost**|REST APIs are more expensive than HTTP APIs.|
|**Cold starts**|When integrated with Lambda, initial request latency may be higher.|
|**Throttling by default**|Must manage usage plans to avoid disruptions.|
|**Payload size limits**|Default max payload = 10 MB.|
|**Caching is REST-only**|HTTP APIs do not support caching as of now.|
# Cost 
It follows pay-as-you-go model

|Component|REST API (USD)|HTTP API (USD)|WebSocket API (USD)|
|---|---|---|---|
|**Requests (1M)**|~$3.50|~$1.00|~$1.00|
|**Data Transfer (per GB)**|Based on AWS standard rates|Same|Same|
|**Caching (optional)**|~$0.02/hour/GB|Not supported|Not supported|
|**Custom Domain Mappings**|No extra charge (requires ACM cert)|Same|Same|
