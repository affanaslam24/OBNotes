Question 30:

A solutions architect is designing a two-tier web application. The application consists of a public-facing web tier hosted on Amazon EC2 in public subnets. The database tier consists of Microsoft SQL Server running on Amazon EC2 in a private subnet. Security is a high priority for the company.

How should security groups be configured in this situation? (Select TWO.)


In this scenario an inbound rule is required to allow traffic from any internet client to the web front end on SSL/TLS port 443. The source should therefore be set to 0.0.0.0/0 to allow any inbound traffic.

To secure the connection from the web frontend to the database tier, an outbound rule should be created from the public EC2 security group with a destination of the private EC2 security group. The port should be set to 1433 for MySQL. The private EC2 security group will also need to allow inbound traffic on 1433 from the public EC2 security group.

This configuration can be seen in the diagram:

![](https://img-c.udemycdn.com/redactor/raw/2020-05-21_01-31-06-6dcaf8d88c9ec27f837343a0ae2630f9.jpg)

**CORRECT:** "Configure the security group for the web tier to allow inbound traffic on port 443 from 0.0.0.0/0 and to allow outbound traffic on port 1433 to the RDS" is a correct answer.

**CORRECT:** "Configure the security group for the database tier to allow inbound traffic on port 1433 from the security group for the web tier" is also a correct answer.

**INCORRECT:** "Configure the security group for the web tier to allow outbound traffic on port 443 from 0.0.0.0/0" is incorrect as this is configured backwards.

**INCORRECT:** "Configure the security group for the database tier to allow outbound traffic on ports 443 and 1433 to the security group for the web tier" is incorrect as the MySQL database instance does not need to send outbound traffic on either of these ports.

**INCORRECT:** "Configure the security group for the database tier to allow inbound traffic on ports 443 and 1433 from the security group for the web tier" is incorrect as the database tier does not need to allow inbound traffic on port 443.



---


A silicon valley based startup has a two-tier architecture using Amazon EC2 instances for its flagship application. The web servers (listening on port 443), which have been assigned security group A, are in public subnets across two Availability Zones (AZs) and the MSSQL based database instances (listening on port 1433), which have been assigned security group B, are in two private subnets across two Availability Zones (AZs). The DevOps team wants to review the security configurations of the application architecture.

As a solutions architect, which of the following options would you select as the MOST secure configuration? (Select two)



**For security group A: Add an inbound rule that allows traffic from all sources on port 443. Add an outbound rule with the destination as security group B on port 1433**

**For security group B: Add an inbound rule that allows traffic only from security group A on port 1433**

A security group acts as a virtual firewall that controls the traffic for one or more instances. When you launch an instance, you can specify one or more security groups; otherwise, we use the default security group. You can add rules to each security group that allows traffic to or from its associated instances. You can modify the rules for a security group at any time; the new rules are automatically applied to all instances that are associated with the security group. When we decide whether to allow traffic to reach an instance, we evaluate all the rules from all the security groups that are associated with the instance.

The following are the characteristics of security group rules:

By default, security groups allow all outbound traffic.

Security group rules are always permissive; you can't create rules that deny access.

Security groups are stateful

The MOST secure configuration for the given use case is:

For security group A: Add an inbound rule that allows traffic from all sources on port 443. Add an outbound rule with the destination as security group B on port 1433

The above rules make sure that web servers are listening for traffic on all sources on the HTTPS protocol on port 443. The web servers only allow outbound traffic to MSSQL servers in Security Group B on port 1433.

For security group B: Add an inbound rule that allows traffic only from security group A on port 1433. The above rule makes sure that the MSSQL servers only accept traffic from web servers in security group A on port 1433.

Therefore, both of these options are correct.

Incorrect options:

**For security group A: Add an inbound rule that allows traffic from all sources on port 443. Add an outbound rule with the destination as security group B on port 443** - As the MSSQL based database instances are listening on port 1433, therefore for security group A, the outbound rule should be added on port 443 with the destination as security group B.

**For security group B: Add an inbound rule that allows traffic only from all sources on port 1433** - The inbound rule should allow traffic only from security group A on port 1433. Allowing traffic from all sources will compromise security.

**For security group B: Add an inbound rule that allows traffic only from security group A on port 443** - The inbound rule should allow traffic only from security group A on port 1433 because the MSSQL based database instances are listening on port 1433.


