![[Pasted image 20250402165157.png]]
remember the code:
sudo yum install -y amazon-efs-utils
(and this remind me that in various different services, in some we need to install newer utils and in some we dont, so make note of that. Like, in cloudwatch agent. but in s3 you need to give role acess. So various ways of doing things. LEARN those various methods and differences.)

 /etc/fstab for boot volume config at moutnitng at the boot time


We need the vpc for this file system to be configured into.

In the network settings we will have mount targets.
usually we put the mount target as all the availibility zones inside the vpc. NOTE: the availibility zones, not the subnets.
And then we choose specific Subnets inside which we need to store our mount tragets.
In our case we chose Application subnets.


**Make sure the security groups are attached in such a way that the instances trying to access this will be able to access it.**
Security groups of the attached instance can be added to the security groups of the instances, in that way both the instances can be attached even with different IPs onfigured to them.

Learn the difference between ebs and efs.

![[Pasted image 20250402172425.png]]


![[Pasted image 20250402172444.png]]
