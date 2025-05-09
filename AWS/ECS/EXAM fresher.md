- With the Fargate launch type, you pay for the amount of vCPU and memory resources that your containerized application requests. vCPU and memory resources are calculated from the time your container images are pulled until the Amazon ECS Task terminates, rounded up to the nearest second. With the EC2 launch type, there is no additional charge for the EC2 launch type. You pay for AWS resources (e.g. EC2 instances or EBS volumes) you create to store and run your application.
---

Amazon ECS uses the AWS Application Auto Scaling service to scales tasks. This is configured through Amazon ECS using Amazon ECS Service Auto Scaling.

A Target Tracking Scaling policy increases or decreases the number of tasks that your service runs based on a target value for a specific metric. For example, in the image below the tasks will be scaled when the average CPU breaches 80% (as reported by CloudWatch):

![[Pasted image 20250416102622.png]]

