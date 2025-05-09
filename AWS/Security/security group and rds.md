DO A PRACTICAL ON THIS ONE BITCH

- First note, that the alb and ec2 are connected, but the security group must be allowed for nerwork transactions.
- Also, since its the rds that is supposed to expose its port so that people can connect to it, we will have to open inbound traffic at port 5432.
- its like when we create an html page and open the port 80.

An HTTP application is deployed on an Auto Scaling Group, is accessible from an Application Load Balancer (ALB) that provides HTTPS termination, and accesses a PostgreSQL database managed by Amazon RDS.

How should you configure the security groups? (Select three)


- **The security group of Amazon RDS should have an inbound rule from the security group of the Amazon EC2 instances in the Auto Scaling group on port 5432**

- **The security group of the Amazon EC2 instances should have an inbound rule from the security group of the Application Load Balancer on port 80**

- **The security group of the Application Load Balancer should have an inbound rule from anywhere on port 443**

A security group acts as a virtual firewall that controls the traffic for one or more instances. When you launch an instance, you can specify one or more security groups; otherwise, we use the default security group. You can add rules to each security group that allows traffic to or from its associated instances. You can modify the rules for a security group at any time; the new rules are automatically applied to all instances that are associated with the security group. When we decide whether to allow traffic to reach an instance, we evaluate all the rules from all the security groups that are associated with the instance.

The following are the characteristics of security group rules: 1. By default, security groups allow all outbound traffic. 2. Security group rules are always permissive; you can't create rules that deny access. 3. Security groups are stateful

PostgreSQL port = 5432 HTTP port = 80 HTTPS port = 443

The traffic goes like this : The client sends an HTTPS request to ALB on port 443. This is handled by the rule - "The security group of the Application Load Balancer should have an inbound rule from anywhere on port 443"

The Application Load Balancer then forwards the request to one of the Amazon EC2 instances. This is handled by the rule - "The security group of the Amazon EC2 instances should have an inbound rule from the security group of the Application Load Balancer on port 80"

The Amazon EC2 instance further accesses the PostgreSQL database managed by Amazon RDS on port 5432. This is handled by the rule - "The security group of Amazon RDS should have an inbound rule from the security group of the Amazon EC2 instances in the Auto Scaling group on port 5432"

Incorrect options:

**The security group of the Application Load Balancer should have an inbound rule from anywhere on port 80** - The client sends an HTTPS request to ALB on port 443 and not on port 80, so this is incorrect.

**The security group of the Amazon EC2 instances should have an inbound rule from the security group of the Amazon RDS database on port 5432** - The security group of the Amazon EC2 instances should have an inbound rule from the security group of the Application Load Balancer and not from the security group of the Amazon RDS database, so this option is incorrect.

**The security group of Amazon RDS should have an inbound rule from the security group of the Amazon EC2 instances in the Auto Scaling group on port 80** - The Amazon EC2 instance further accesses the PostgreSQL database managed by Amazon RDS on port 5432 and not on port 80, so this option is incorrect.