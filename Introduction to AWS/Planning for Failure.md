# Storage
When a file is stored in Amazon S3, the file is redundantly copied into every Availability Zone ([[AWS Global Infrastructure#Availability Zone]]) in that Region ([[AWS Global Infrastructure#Region]]). If 1 AZ goes down, you still have 2 copies of that file available for you to use
# Compute
It is best practice to spread out your computing resources across multiple AZ to guarantee high availability. So if 1 AZ goes down, your architecture is still up and running 
# Database
Config your database for Multi-AZ deployment. If your AZ with your primary database fails, one of the standby databases in a healthy AZ automatically becomes your new primary DB. Therefore, your architecture is still functioning 
