#services 

**Elastic Load Balancing (ELB)** is a **[[highly available]]** and **[[scalable]]** AWS service that automatically distributes incoming network or application traffic across multiple targets, such as **[[Amazon EC2]] instances**, **containers**, or **IP addresses**, within one or more availability zones.

# ELB Options
## Application Load Balancer
An Application Load Balancer is **ideal for load balancing HTTP and HTTPS traffic**. It operates at the **request level (7 layer of OSI model)** and routes traffic to targets (EC2 instances, containers, IP addresses, and Lambda functions) based on the request content. Choose an Application Load Balancer when you need a flexible feature set for your applications with HTTP and HTTPS traffic.
## Network Load Balancer
A Network Load Balancer is **ideal for load balancing TCP and UDP traffic**. Choose a Network Load Balancer when you need ultra-high performance and static IP addresses for your applications. Operating at the **connection level (layer 4 of OSI model)**, Network Load Balancers are capable of handling millions of requests per second securely while maintaining ultra-low latencies.
## Gateway Load Balancer
A Gateway Load Balancer helps you to **deploy, scale, and manage your third-party virtual appliances**. It operates at the **network level (level 3 of OSI model)** and provides a gateway for distributing traffic across multiple virtual appliances while scaling
them up and down based on demand.

Choose a Gateway Load Balancer when you need to deploy and manage a fleet of third-party virtual appliances that support GENEVE protocols. You can use these appliances to improve security, compliance, and policy controls. Gateway Load Balancers operate at the third layer.

# Additional Options
## EC2 Instance Connect
Amazon EC2 Instance Connect provides a simple and secure way to connect to your instances by using Secure Shell (SSH)
You can connect by using Amazon EC2 Instance connect with a valid username and without a key pair
## Session Manager
Session Manager is a fully-managed AWS Systems Manager capability. You can use it
to manage your EC2 instances, on-premises instances, and virtual machines through an
interactive one-click, browser-based shell or through the AWS CLI.
Fleet Manager, an AWS Systems Manager capability, is a unified Ul experience that
helps you remotely manage your nodes that run on AWS or on premises. With Fleet
Manager, you can view the health and performance status of your entire server fleet
from one console.
To connect to an instance by using Session Manager, you must be granted the
necessary permissions.
## SSH Client
After launching your instance, you can connect to it and use it the way that you'd use a
computer that's sitting in front of you. If the instance is created without a key pair, you
cannot connect to the instance through SSH.
## EC2 Serial Console
The Amazon EC2 serial console provides access to your EC2 instance's serial port. You
can use the serial console to troubleshoot boot, network configuration, and other
issues. The serial console does not require your instance to have any networking
capabilities. On the serial console, you can enter commands to an instance as if your
keyboard and monitor are directly attached to the instance's serial port.
To connect to an instance by using the Amazon EC2 serial console, the account must be
authorized in the Amazon EC2 account settings.