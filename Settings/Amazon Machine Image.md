# Amazon Machine Image components:
- **Templates** for the root volume of the instance contain the following:
	- Operating system (OS)
	- Application servers
	- Applications
+ **Launch permissions** control which AWS accounts can use the AMI.
+ **Block device mapping** specifies the volumes to attach to the instance (if any) when it is launched.

# Using AMIs
+ Choose an AMI that fits the use case of your instance.
+ Use the same AMI to launch multiple instances that should have the **SAME configuration**.
+ If instances have different use cases, use AMIs that are specific to the use cases of each instance.

***After an instance is created, you CANNOT change the AMI !***
# Where do you get an AMI?
## Pre-built
Amazon offers a number of pre-built AMIs to launch your instances. These AMIs include Linux and Windows options with various suboptions to tailor your setup 
## AWS Marketplace
The AWS Marketplace offers a digital catalog with thousands of software solutions listed. These AMIs can offer specific use cases to help you get started quickly.
## Create your own
Create your own: An AMI is an anonymized, block-level copy of the root volume of a donor machine or golden instance. It is a virtual machine (VM) that you configured with the specific OS and application content that you want placed on the AMI. When you create an AMI, Amazon EC2 stops the instance, snapshots its root volume, and finally registers the snapshot as an AML.
## Community AMIs
Community AMIs: People all over the globe create community AMIs. These AMIs are not vetted by AWS and are used at your own risk. These AMIs can offer many different solutions to various problems, but use them with great care. They should be thoroughly reviewed for security concerns when using them in any production or corporate environment.

# AMI Benefits
- **Repeatability:** Instances that are launched from the same AMI are **exact replicas of one another**. As a result, it greatly facilitates building clusters of similar instances or recreating compute environments.
- **Reusability:** AMIs package the full configuration and content of an EC2 instance such that it **can be used over and over again**, with efficiency and precision.
- **Recoverability:** An AMI is perfect for replacing failed machines with new instances that are created from the same AMI.
- **Marketplace solutions:** Suppose that you are looking for a software solution from a specific vendor. An AMI probably exists on the marketplace that you can launch to implement that solution on an EC2 instance. Additionally, authorized software vendors can create AMIs and also sell them there.
- **Backups:** AMIs provide a great way to back up a complete EC2 instance configuration, which you can use to launch a replacement instance in the event of a failure.