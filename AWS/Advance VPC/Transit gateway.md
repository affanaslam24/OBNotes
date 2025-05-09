![[Pasted image 20250409222701.png]]


without transit gateway:
![[Pasted image 20250409222829.png]]

but for fully highly available:
![[Pasted image 20250409222924.png]]



Now, with transit gateway:
![[Pasted image 20250409223147.png]]
- notice that the attachments are inside the subnet of The Az where the service is required.
- Its similar to the interface endpoint where a subnet was selected in an AZ. thats where it resides, BUT other subnets can access it.
- it can transitive routing btween different services, as you can see.
- provides global network.



![[Pasted image 20250409223417.png]]


remeber these for exam.


DeMO:
[[transit practical]]


----


AWS Transit Gateway connects VPCs and on-premises networks through a central hub. With AWS Transit Gateway, you can quickly add Amazon VPCs, AWS accounts, VPN capacity, or AWS Direct Connect gateways to meet unexpected demand, without having to wrestle with complex connections or massive routing tables. This is the operationally least complex solution and is also cost-effective.

The image below depicts how transit gateway can assist with simplifying network deployments:

![](https://img-c.udemycdn.com/redactor/raw/test_question_description/2020-11-27_10-12-08-05293542d6a09dfb24fcf7e9a59f123e.jpg)

**CORRECT:** "Configure AWS Transit Gateway between the accounts. Assign Direct Connect to the transit gateway and route network traffic to the on-premises servers" is the correct answer.

**INCORRECT:** "Create a VPN connection between each new account and the Direct Connect VPC. Route the network traffic to the on-premises servers" is incorrect. You cannot connect VPCs using AWS managed VPNs and would need to configure a software VPN and then complex routing configurations. This is not the best solution.

**INCORRECT:** "Create a Direct Connect connection in each new account. Route the network traffic to the on-premises servers" is incorrect. This is an expensive solution as you would need to have multiple Direct Connect links.

**INCORRECT:** "Configure VPC endpoints in the Direct Connect VPC for all required services. Route the network traffic to the on-premises servers" is incorrect. You cannot create VPC endpoints for all services and this would be a complex solution for those you can.