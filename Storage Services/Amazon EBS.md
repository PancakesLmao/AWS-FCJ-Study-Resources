#storage #services 
Amazon Elastic Block Store is a durable, detachable, high-performance, **block-storage** service **designed for Amazon EC2**
Works like external Hard drive
Can provide low latency
Able to handle almost any computing requirements

# Volume Types
## General purpose
General purpose is an SSD volume that **balances price and performance** for a wide variety of workloads. 
Its use cases include the following:
+ Recommended for most workloads
+ Virtual desktops
+ Medium-sized single instance databases such as Microsoft SQL Server and Oracle
+ Latency-sensitive interactive applications
+ Boot volumes
+ Development and test environments
## Provisioned IOPS
Input/Output Operations per Second (IOPS) measures the number of maximum reads and writes that a computing storage device can perform in a second. Provisioned IOPS are **the highest-performance SSD volumes for mission-critical low-latency or high-throughput workloads**. With these volumes, customers can meet the IOPS and throughput requirements of their most intensive business-critical applications.

Its use cases include the following:
- Critical business applications that require sustained IOPS performance
- Large database workloads
## Throughput optimized
Throughput Optimized is a **low-cost HDD volume** designed for frequently accessed, throughput-intensive workloads 
Its use cases include the following:
- Streaming workloads
- Big data
- Data warehouses
- Log processing
- Cannot be a boot volume
## Cold
Cold HDD is **the lowest cost HDD volume** and is designed for less frequently accessed workloads.
Its use cases include the following: 
+ Throughput-oriented storage for large volumes of data that is infrequently accessed
+ Scenarios where the lowest storage cost is important
+ Cannot be a boot volume

# Configuration options
## Volume types
When choosing a volume type, you cannot use Throughput Optimized or Cold HDD volumes for root volumes.
The root volume must be a general purpose or a Provisioned IOPs volume. You can add additional volumes (non-root volumes) to your instance and mix and match any types with other volume types as needed.
## Volume size
The size of the volume is chosen in GiB. If you are creating the volume from a snapshot, then the size of the volume cannot be smaller than the size of the snapshot.
Supported volume sizes are as follows: 
- General purpose volumes: 1 GiB to 16,384 GiB
- Provisioned IOPS: 4 GiB to 16,384 GiB
- Throughput Optimized or Cold HHD: 125 GiB to 16,384 GiB
## Delete on termination
Delete on termination indicates whether the volume should be automatically deleted when the instance is terminated. If you disable this delete on termination, then the volume will persist independently from the running life of an EC2 instance. As a result, **the volume will remain provisioned in your account** until you delete it manually.

You can also change the delete on termination behaviour after the instance has been launched.
## Encryption
Amazon EBS encryption **IS** an encryption solution for your EBS volumes. You **have the option to encrypt your root volume** and any additional volumes that you attach to your EC2 instance. Amazon EBS encryption uses **AWS Key Management Service** ([[AWS KMS)]] keys to encrypt volumes. AWS KMS is a security service that lets you create and manage cryptographic keys and control their use across a wide range of AWS services.

# [[Amazon EFS]]