![[Screenshot from 2025-03-30 01-32-17.png]]
- Its region resilient and are always cnnectwed to a VPC
- one vpc can have 0 (private vpc) or 1 (public) igw.
- one igw can be attached to 0 or 1 vpc.
- It stays in the public zone of aws.

### Working
![[Screenshot from 2025-03-30 01-32-46.png]]

Create a custom route table, attach it to the subnet using association, make sure that the routing goes from igw.


**WHAT kind of routing, like how does it do? also, i know the higher prefix, the more priority, so how do you write the specific ips in it? properly show the different ip mapping inside a route table**

![[Screenshot from 2025-03-30 01-30-16.png]]
Like in this, the /16 is the vpc's cidr block, so this is saying any ip call in between this range, the subnets willl do the internal talking between themselves.
And if we put a 0.0.0.0/0 and target as igw, then that means any propogation, apart from /16 vpc ones, will go to the public zone.

Go to [[stateful and stateless]] next.


![[Screenshot from 2025-03-30 01-37-16.png]]
Its the IGW that does the private to public mapping. even for natgateways. Check out in the nat gateway notes.
The instances only know privste ips, at the samw times, since all the subnets only have privste ips insid ethe vpc, they can communicate easily. And then we have the public ip assigned at the igw level.
Check out [[NAT GATEWAY]] to understand different routing styles. 

### What are jumpboxes and shit
![[Screenshot from 2025-03-30 01-38-55.png]]

