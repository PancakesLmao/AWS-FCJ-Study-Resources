#services 

1 Amazon EC2 Auto Scaling helps you maintain application availability and lets you automatically
add or remove EC2 instances according to conditions that you define.

- Launches or terminates instances based on specified conditions
- Automatically registers new instances with load balancers when specified
- Can launch instances across Availability Zones
* Replaces unhealthy or unreachable instances with new instances
* Helps to save money by automating the number of instances based on condition needs

# Scaling Options
## Schedule scaling
Scheduled scaling is **based on a schedule** so that you can scale your application ahead of known load changes. For example, every week the traffic to your web application starts to increase on Wednesday, remains high on Thursday, and starts to decrease on Friday. You can plan your scaling activities based on the known traffic patterns of your web application.
## Dynamic Scaling
Dynamic scaling lets you **follow the demand curve for your applications** closely, which reduces the need to manually provision Amazon EC2 capacity in advance. Thus, you can use target tracking scaling policies to select a metric for your application, such as CPU utilization. For example, when CPU utilization reaches a threshold that you specify, Amazon EC2 Auto Scaling will then automatically add more instances. And when the CPU utilization drops below the threshold that you specify, Amazon EC2 Auto Scaling will terminate the extra instances.
## Predictive Scaling
Predictive scaling **uses machine learning to schedule** the right number of EC2 instances in anticipation of approaching traffic changes. Predictive scaling uses machine learning algorithms to predict future traffic, including regularly occurring spikes, and provisions the right number of EC2 instances in advance. As a result, it removes the need for manual adjustment to Amazon EC2 Auto Scaling parameters. It also delivers faster, simpler, and more accurate capacity provisioning, which results in lower cost and more responsive applications.
