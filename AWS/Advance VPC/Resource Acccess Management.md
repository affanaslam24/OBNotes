You have multiple AWS accounts within a single AWS Region managed by AWS Organizations and you would like to ensure all Amazon EC2 instances in all these accounts can communicate privately. Which of the following solutions provides the capability at the CHEAPEST cost?


- with a transit gateway, each account would have to have a transit gateway, nbut using this RAM solution you can have one VPC and expose its subnet using RAM. 

**Create a virtual private cloud (VPC) in an account and share one or more of its subnets with the other accounts using Resource Access Manager**


You have **multiple AWS accounts**, and you want **EC2 instances in each account to talk to each other privately**, **without going over the internet**, and you want to **do it cheaply**.

RAM-Based Solution (VPC Sharing):

**Think of this like:**
- You have **one big house (a VPC)** owned by **Account A**.
- You let your **friends (other AWS accounts)** come live in some of the **rooms (subnets)** of this house.
- Since everyone is under **one roof (same VPC)**, they can talk to each other **freely and privately**.

- **Account A** creates a **VPC** (with public/private subnets, routing, etc.).
- Account A **shares one or more subnets** from this VPC with **other accounts (say, Account B, C, etc.)** using **AWS RAM**.    
- **Account B and C** don’t create their own VPCs. Instead, they **launch their EC2 instances directly into the shared subnets** from Account A’s VPC.
- All EC2s — even though they belong to **different accounts** — are in the **same network (VPC)** and can talk **privately over private IP**.
---
AWS Resource Access Manager (RAM) is a service that enables you to easily and securely share AWS resources with any AWS account or within your AWS Organization. You can share AWS Transit Gateways, Subnets, AWS License Manager configurations, and Amazon Route 53 Resolver rules resources with RAM. RAM eliminates the need to create duplicate resources in multiple accounts, reducing the operational overhead of managing those resources in every single account you own. You can create resources centrally in a multi-account environment, and use RAM to share those resources across accounts in three simple steps: create a Resource Share, specify resources, and specify accounts. RAM is available to you at no additional charge.

The correct solution is to share the subnet(s) within a VPC using RAM. This will allow all Amazon EC2 instances to be deployed in the same VPC (although from different accounts) and easily communicate with one another.

How AWS Resource Access Manager (AWS RAM) Works:

![](https://d1.awsstatic.com/products/RAM/product-page-diagram_AWS-Resource-Access-Manager(1).379df75d48a8e2cc6160859b7ca3626a9b9be0c1.png)

via - [https://aws.amazon.com/ram/](https://aws.amazon.com/ram/)

Incorrect options:

**Create a Private Link between all the Amazon EC2 instances** - AWS PrivateLink simplifies the security of data shared with cloud-based applications by eliminating the exposure of data to the public Internet. AWS PrivateLink provides private connectivity between VPCs, AWS services, and on-premises applications, securely on the Amazon network. Private Link is a distractor in this question. Private Link is leveraged to create a private connection between an application that is fronted by an NLB in an account, and an Elastic Network Interface (ENI) in another account, without the need of VPC peering and allowing the connections between the two to remain within the AWS network.

**Create a VPC peering connection between all virtual private cloud (VPCs)** - A VPC peering connection is a networking connection between two VPCs that enables you to route traffic between them using private IPv4 addresses or IPv6 addresses. Instances in either VPC can communicate with each other as if they are within the same network. You can create a VPC peering connection between your VPCs, or with a VPC in another AWS account. The VPCs can be in different regions (also known as an inter-region VPC peering connection). VPC peering connections will work, but won't efficiently scale if you add more accounts (you'll have to create many connections).

**Create an AWS Transit Gateway and link all the virtual private cloud (VPCs) in all the accounts together** - AWS Transit Gateway is a service that enables customers to connect their Amazon Virtual Private Clouds (VPCs) and their on-premises networks to a single gateway. A Transit Gateway will work but will be an expensive solution. Here we want to minimize cost.

References:

[https://](https://aws.amazon.com/ram/)


