A company hosts a monolithic web application on an Amazon EC2 instance. Application users have recently reported poor performance at specific times. Analysis of Amazon CloudWatch metrics shows that CPU utilization is 100% during the periods of poor performance.  
The company wants to resolve this performance issue and improve application availability.

**Which combination of steps will meet these requirements MOST cost-effectively? (Select TWO.)**



	**Use AWS Compute Optimizer to obtain a recommendation for an instance type to scale vertically:** This is correct because AWS Compute Optimizer can suggest a more appropriate EC2 instance type with adequate resources for improved performance when scaling vertically.

**Create an Auto Scaling group and an Application Load Balancer to scale horizontally:** This is correct because horizontal scaling improves application availability by adding multiple EC2 instances. The Application Load Balancer ensures traffic is distributed evenly across instances.

**Create an Amazon Machine Image (AMI) from the web server. Reference the AMI in a new launch template:** This is incorrect because creating an AMI and a launch template alone does not address scaling or performance issues without integrating them into an Auto Scaling group.

**Create an Auto Scaling group and an Application Load Balancer to scale vertically:** This is incorrect because vertical scaling is achieved by changing the instance type, not by using Auto Scaling groups or load balancers.

**Use AWS Compute Optimizer to obtain a recommendation for an instance type to scale horizontally:** This is incorrect because horizontal scaling focuses on adding multiple instances, which does not require Compute Optimizer recommendations for instance types.


---



When you hibernate an instance, AWS signals the operating system to perform hibernation (suspend-to-disk). Hibernation saves the contents from the instance memory (RAM) to your Amazon EBS root volume. AWS then persists the instance's Amazon EBS root volume and any attached Amazon EBS data volumes.

When you start your instance:

The Amazon EBS root volume is restored to its previous state

The RAM contents are reloaded

The processes that were previously running on the instance are resumed

Previously attached data volumes are reattached and the instance retains its instance ID

Overview of Amazon EC2 hibernation:

![](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/images/hibernation-flow.png)

via - [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Hibernate.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Hibernate.html)

By using Amazon EC2 hibernate, we have the capability to resume it at any point of time, with the application already launched, thus helping us cut the 3 minutes start time.

Incorrect options:

**Use Amazon EC2 User-Data** - Amazon EC2 instance user data is the data that you specified in the form of a configuration script while launching your instance. Here, the problem is that the application takes 3 minutes to launch, no matter what. EC2 user data won't help us because it's just here to help us execute a list of commands, not speed them up.

**Use Amazon EC2 Meta-Data** - Amazon EC2 instance metadata is data about your instance that you can use to configure or manage the running instance. Instance metadata is divided into categories, for example, host name, events, and security groups. The EC2 meta-data is a distractor and can only help us determine some metadata attributes on our EC2 instances.

**Create an Amazon Machine Image (AMI) and launch your Amazon EC2 instances from that** - An Amazon Machine Image (AMI) provides the information required to launch an instance. You must specify an AMI when you launch an instance. You can launch multiple instances from a single AMI when you need multiple instances with the same configuration. You can use different AMIs to launch instances when you need instances with different configurations.

Creating an AMI may help with all the system dependencies, but it won't help us with speeding up the application start time.

References: