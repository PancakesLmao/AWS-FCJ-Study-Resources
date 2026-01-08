#services 

# What is Infrastructure as Code (IaC) ?
Infrastructure as Code is a **practice** where infrastructure is provisioned and managed **using code** and software development techniques, rather than manual processes. It treats servers, networks, databases, and other resources as configurable software, enabling automation, version control, and repeatability. IaC tools allow you to define infrastructure in files (e.g., declarative or imperative code), which can be stored in version control systems like Git, reviewed via pull requests, and deployed consistently across environments.

# AWS CloudFormation
AWS CloudFormation is a service that helps you model, provision, and manage AWS and third-party resources using code. It allows you to create templates that describe your infrastructure, which CloudFormation then uses to create and configure resources automatically. As an IaC tool, it's declarative—you specify what you want, and CloudFormation handles the how. It integrates seamlessly with other AWS services and supports over 1,000 resource types.
## Template
A **CloudFormation template** is a text file written in either **YAML or JSON** format. This file acts as a _blueprint_ for your infrastructure: it tells AWS exactly what resources you want, how you want them configured, and how they relate to one another.
### Template Components
- **AWSTemplateFormatVersion:** Specifies the template format version (e.g., "2010-09-09" for standard capabilities; rarely changes).
- **Description**: A short explanation of what the template does (optional, for documentation).
- **Parameters**: Lets users pass in values at runtime when launching or updating a stack—for example, choosing instance types, environment names, or custom settings. This makes templates reusable and customizable without edits.
- **Mappings**: A lookup table for conditional values (e.g., mapping instance types to AWS Regions or environments). Use with Fn::FindInMap for dynamic lookups.
- **Conditions**: Allows you to control whether resources are created or properties assigned based on parameters or situations (e.g., create a database only in production environments).
- **Resources**: The _most important part_ (required). Lists the AWS resources to create, such as EC2 instances, S3 buckets, Lambda functions, and more. Each has a unique logical ID, type, and properties.
- **Outputs**: Shows values after creation—such as URLs, IPs, ARNs, or resource IDs. Useful for cross-stack references or integration with other systems.
- **Metadata**: Includes extra information or labels for documentation and organization (optional, less commonly used).
- **Transform**: Applies macros or integrations, like AWS SAM for serverless apps (transforms SAM syntax to CloudFormation) or AWS::Include for external snippets.
- **Rules**: Validates parameter values or combinations during stack creation/updates based on custom conditions (optional).​
## Stacks
CloudFormation groups all related resources into a stack, which you can create, update, or delete as a single unit. 
Use StackSets for managing stacks across multiple AWS accounts and Regions with a single template.
## Use Cases
- Automating application deployments
- Disaster recovery setups
- Multi-region infrastructures

## Integration with AWS
| AWS Service                 | CloudFormation Role                                                      |
| --------------------------- | ------------------------------------------------------------------------ |
| **IAM**                     | Access control for stack operations and resource provisioning.           |
| **CloudWatch**              | Monitoring with Rollback Triggers; alarms for automated error handling.  |
| **Config**                  | Compliance and drift detection integration.                              |
| **CDK**                     | Programmatic template generation and direct provisioning.                |
| **SAM**                     | Serverless app modeling with automatic transformation to CloudFormation. |
| **CloudFormation Designer** | Visual template editing and diagramming.                                 |
| **StackSets**               | Multi-account/region management (integrates with AWS Organizations).     |
| **S3/EC2/Lambda**           | Core resource provisioning (e.g., buckets, instances, functions).        |
| **OpsWorks/ECS**            | Orchestration for app deployments and container services.                |
| **Quick Starts**            | Pre-built templates for common architectures.                            |
## Use Cases
- Automating application deployments (e.g., single EC2 instances to multi-tier apps).
- Multi-region/multi-account infrastructures with StackSets.
- Disaster recovery setups with consistent, repeatable provisioning.
- CI/CD pipelines: Integrate with CodePipeline for testing/deploying templates.
- Serverless apps: Use SAM for functions, APIs, and databases.
- Governance: Enforce policies across organizations with hooks and drift detection.
## Cost
AWS CloudFormation is **generally free to use**—you pay only for the underlying AWS resources it provisions (e.g., EC2 instances, S3 storage) at standard rates, as if created manually. No upfront fees, minimum commitments, or charges for core operations like creating/updating/deleting stacks with AWS-native resources (AWS::* or Alexa::* namespaces).

**Third-Party Resource Providers & Custom Hooks (Updated Nov 2025)**:

- **Handler Operations**: $0.0009 per operation (CREATE/UPDATE/DELETE/READ/LIST) beyond free tier.
- **Free Tier**: First 1,000 operations/month free (includes third-party and hooks).
- **Duration**: First 30 seconds free per operation; $0.00008/sec beyond.
- **Data Transfer**: Standard AWS rates apply.
- No charges for AWS-managed hooks (AWS::*).
- Examples: Managing 500 third-party resources daily (15,000 ops) costs ~$12.60/month after free tier.
- Use AWS Pricing Calculator for estimates.

Pay-as-you-go for extensions; core service remains free.

# AWS CDK
[[AWS CDK]]

