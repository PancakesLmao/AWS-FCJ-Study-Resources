# Instance Families
Each instance belongs to an instance family. **An instance family is a group of instances, with varying configurations**, which are based on similar compute, memory, and storage capabilities.
T/M/C/P/R family 
# Instance type names
t3.large
**t** - the family name
**3** - the generation number
**large** - the size of the instance

## [[Amazon Machine Image]] (AMI)
# Instance Categories
## General purpose
Instance types: **A1, M4, M5, T2, T3**
Use Case: General purpose instances provide **a balance of compute, memory, and networking resources**, and can be used for a variety of diverse workloads. These instances are ideal for applications that use these resources in equal proportions, such as web servers and code repositories.
## Compute optimized
Instance types: **C4, C5**
Use Case: Compute optimized instances are ideal for compute bound applications that benefit from **high performance processors**. Instances that belong to this family are well suited for batch processing workloads, media transcoding, machine learning inference, and other compute-intensive applications.
## Memory optimized
Instance types: **R4, R5, X1, Z1**
Use Case: Memory optimized instances are designed to deliver fast performance for workloads that process large data sets in memory.
## Accelerated Computing
Instance types: **F1, G3, G4, P2, P3**
Use Case: Accelerated computing instances use **hardware accelerators, or co-processors, to perform functions such as floating point number calculations, graphics processing, or data pattern matching**. They perform such functions more efficiently than is possible in software that is running on CPUs.
## Storage optimized
Instance types: **D2, H1, I3**
Use Case: Storage optimized instances are designed for workloads that require **high, sequential read and write access to very large data sets on local storage**. They are optimized to deliver tens of thousands of low-latency, random 1/0 operations per second (I0PS) to applications.

# Scaling Instances Vertically 
Unlike the instance's AMI, ***the instance types can be changed after the instance is launched***. Thus, you have to option to scale your instances by changing your instance type to give it more compute power. This kind of expansion is called **VERTICAL SCALING**
Vertical scaling (scaling for more compute power per instance) give you the ability to:
- Scale up or down for CPU
- Switch to any **instance type in any instance family**

# Instance Costs
5 main driver that affect the instance cost: 
## Instance purchasing options
### On-demand Instances
With On-Demand instances, you **pay for instances only for the amount of time that you use them**. No long-term commitments or upfront payments are required. You can increase or decrease your compute capacity depending on the demands of your application and pay only for the time that you use them. 
**Use case:** Short-term computing workloads that cannot be interrupted; and users that need low-cost computing without any upfront or long-term commitment.
### Spot Instances
You can use Amazon EC2 Spot Instances to **take advantage of unused Amazon EC2 capacity** in the AWS cloud for a discount. You can save **up to 90 PERCENT** compared to On-Demand prices. To get a Spot Instance, you submit a request with the instance specifications and the maximum price that you are willing to pay per hour. When a Spot Instance is available at your submitted price, you will have access to the instance. 
Spot blocks: Launch spot instances with a duration lasting 1-6 hours
**Use case:** Workloads that can be paused and restarted when computing prices meet your budget for Spot Instances.
### Reserved Instances (RI)
Reserved Instances provide you with a significant discount (up to **72 PERCENT**) compared to On-Demand Instance pricing. With Reserved Instances, you commit to paying for the instance for 1 or 3 years, depending on the conditions you agree to when purchasing them. 
Three upfront payment methods: 
+ Standard RIs 
+ Convertible Rls 
+ Scheduled Rls 
**Use case:** Computing needs with a steady amount usage of up to 1 year or more (Long time workload).

### Compute Savings Plans
- Compute Savings Plans provide the most flexibility and help to reduce your costs by **up to 66 PERCENT**. These plans automatically apply to EC2 instance usage regardless of instance family, size, Availability Zone, Region, operating system, or tenancy. They also apply to AWS Fargate and AWS Lambda usage.
- EC2 Instance Savings Plans apply to a specific instance family within a specific Region and provide the largest discount (up to **72 PERCENT**, like Standard Rls)
**Use case:** Long time workloads, Computing needs that might need flexibility over location or by instance power
## Tenancy 
Tenancy defines how EC2 instances are distributed across the physical host hardware.
Amazon EC2 offers three tenancy options for hosting your instances. The tenancy that you choose will affect pricing.
- Shared tenancy
- Dedicated instance
- Dedicated host

| Tenancy Attributes                                                                  | Dedicated Host                                 | Dedicated Instance | Shared Tenancy |
| ----------------------------------------------------------------------------------- | ---------------------------------------------- | ------------------ | -------------- |
| Instances share host hardware with instances from other AWS accounts.               | No                                             | No                 | Yes            |
| Instances are isolated on host hardware that is not shared with other AWS accounts. | Yes                                            | Yes                | No             |
| Access to manage instance placement on the host hardware.                           | Yes                                            | No                 | No             |
| Consistently deploy instances to the same physical server over time.                | Yes                                            | No                 | No             |
| Cost per instance.                                                                  | Depends on the number of instances on the host | High               | Low            |
### Use case
| Tenancy use cases                                          | Dedicated Host                                           | Dedicated Instance                                       | Shared Tenancy                     |
|------------------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------|-------------------------------------|
| Regulatory compliance that requires **hosts cannot be shared** between AWS accounts. | **hosts cannot be shared** between AWS accounts.       | **hosts cannot be shared** between AWS accounts.       | **Regulatory compliance is not required.** |
| Managing the host hardware **is** required.                | Managing the host hardware **is not** required.        | Development and testing accounts.                      |
| When you **will need enough** or close to enough dedicated instances to fill a host. | When you **do not need** enough dedicated instances to fill a host. |                                                     |                                     |
| Using **existing** per-socket, per-core, or per-VM software licenses that are **bound** to VMs, sockets, or physical cores, subject to your license terms. |                                                     |                                                     |                                     |

# Optimizing Instance Costs
- **Right-sizing** your instances means that you choose the right balance of instance types. This process includes monitoring when servers can be either sized down or turned off and still meet your performance requirements
- **Increase elasticity** is the practice of designing your deployments to reduce the amount of server capacity that is idle by implementing deployments that are elastic. For example, you can have deployments that use automatic scaling to handle peak loads.
- **Optimal pricing model** is about recognizing the available pricing options. Analyze your usage patterns so that you can run EC2 instances with the right mix of pricing options.
- **Optimizing storage choices** requires you to analyze the storage requirements of your deployments. The goal is to reduce unused storage overhead when possible and choose less expensive storage options if they still meet your requirements for storage performance.