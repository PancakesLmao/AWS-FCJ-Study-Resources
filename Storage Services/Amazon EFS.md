#storage #services 
Amazon Elastic File System (Amazon EFS) is a file system that you can use to share files among multiple EC2 instances. It automatically grow and shrinks as you add add and remove files with no need for management or provisioning. 
You can attach instances to the file system as you launch your instance or afterwards 
You can remove instance from the file system
Amazon EFS **CANNOT act as a root volume**. Each instance that is attached to Amazon EFS must have its own root volume