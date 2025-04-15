![[Pasted image 20250409223555.png]]


1. 
![[Pasted image 20250409223711.png]]
need private ips of the instances, and ping them from all the different instances for each other.
proves that all are isolated.


![[Pasted image 20250409223825.png]]
![[Pasted image 20250409223838.png]]

Now, create attachments:
![[Pasted image 20250409223953.png]]
![[Pasted image 20250409224016.png]]
create attachment for each vpc.
![[Pasted image 20250409224056.png]]
selected the VPC, and **then we need to select the subnet where the interface will be kept**

For each AZ that you use, you need to make sure that one subnet has the interface in it. This is important. **other subnets in that AZ can use it?** idk, but other AZs in that vpc can use this interface? **NOPE**


![[Pasted image 20250409224307.png]]



Now, for the other VPC
![[Pasted image 20250409224336.png]]
![[Pasted image 20250409224346.png]]


NOw onto the route table:
![[Pasted image 20250409224414.png]]

a default route table was created:
- the association, propagation and route tables are created automatically.
![[Screenshot from 2025-04-09 22-44-53.png]]
![[Screenshot from 2025-04-09 22-44-58.png]]
![[Screenshot from 2025-04-09 22-45-02.png]]




Although this is all done, we still dont get the ping response:
![[Pasted image 20250409224616.png]]

this is because the route tables of the vpc are not configured yet:
![[Pasted image 20250409224638.png]]

![[Pasted image 20250409224647.png]]
the route tables needs to be changed


![[Pasted image 20250409224735.png]]
VPC A to VPC B


Now for VPC B to VPC A
![[Pasted image 20250409224802.png]]


### **NOW unlike the VPC peering where we had to configure the security group as well, here we dont need to configure the security group in any way**


This was the part where different vpcs are connected to each other inside the AWs environment.

---
we are skipping the connection with the on premesis one, mostly becaus eits too tiring.
![[Pasted image 20250409225135.png]]
![[Pasted image 20250409225158.png]]


can use sie to site vpn![[Pasted image 20250409225213.png]]
OR



transit gateway attachment directly
![[Pasted image 20250409225300.png]]
this selection of VPN to create an attachment.


![[Pasted image 20250409225446.png]]
select the customer gateway you made


Now, this directly creates:
![[Pasted image 20250409225520.png]]
a site to site vpn connection!!!


But you will have to add the route to the route table of transit gateway by yourself;
![[Pasted image 20250409225622.png]]

Add the attachment and the cidr block of the on prem 
![[Pasted image 20250409225649.png]]

Download the config from the site to site vpn, and etc![[Pasted image 20250409225719.png]]

Then configure your On prem Router and everything

but note this:
![[Pasted image 20250409225759.png]]
these are the remote subnets that are in transit gateway that you need to gain access, so make sure you add them in your on prem route


![[Pasted image 20250409225845.png]]



Then create route table configs:
for 1st vpc
![[Pasted image 20250409225912.png]]

for 2nd vpc
![[Pasted image 20250409225929.png]]



Then go to your vpc routings and change them such that they can access the on prem ips:

![[Pasted image 20250409230021.png]]


![[Pasted image 20250409230028.png]]


DONE!!!!



