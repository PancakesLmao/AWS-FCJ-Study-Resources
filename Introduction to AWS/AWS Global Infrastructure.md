#terms 

![[Pasted image 20250210171542.png]]
# Region
**Physical location around the world where data centers are clustered together**
A group of logical data centers is called an Availability Zone
Each AWS Region consist if multiple, isolated and physically separated Availability Zones within a geographic area
# Availability Zone
An Availability Zone is a **zoned area within a Region that harbor one or more data centers** (typical 3). Availability Zones house all the hardware devices that AWS offers

They are physically separated by a meaningful distance (up to 100km or 60miles) from any other Availability Zone in the Region

Availability Zones are **Interconnected** with high-bandwidth, low-latency networking to provide low-latency networking between zones that is sufficient to accomplish synchronous replication (same time replication)
# Edge Location
Edge locations are connected to the AWS Regions through the AWS network across the globe. They link with tens of thousands of networks for **improved origin fetches and dynamic content acceleration** 

**Edge locations cache copies of your content for faster delivery to user at any location**. They support AWS services like [[Amazon Route 53]] and [[Amazon CloudFront]]

AWS has over 200 edge locations that are placed in 90 cities, across 47 countries

# Why were these exists?
When building your architecture in the cloud, it is important to plan for failure, you want a plan in place to resolve any failures that might occur
> [[Planning for Failure]]

