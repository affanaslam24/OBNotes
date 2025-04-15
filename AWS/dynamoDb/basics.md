- need to be accessed through net
- either through igw or gateway vpc endppoint
- -its a wide column key value database
- its database as a service, not like rds, which is database instsnce as a service.
- **encryption at rest**
- can include event driven changes

![[Pasted image 20250411131741.png]]



- provisioned capacity or on demand capacity
- capacity means speed.
![[Pasted image 20250411133017.png]]
- one prerequisite is: you NEED to have the keys atleast, when its in a table.
- And the size of one item needs to be a max of 400kb



![[Pasted image 20250411133147.png]]
- this is mostly manual backups.
but we have something called **point in time recovery**::
This is something that needs to be enabled explicitly.
![[Pasted image 20250411133502.png]]
- allows you to have any point in time, even seconds before, recovery. Can help you create a **new** table to any point in time.



KEYNOTES:
![[Pasted image 20250411133645.png]]
- no infra cost, no base cost. You only pay for the resources that you use: storage, operations, or capacity requiremens that you set.

YOU CAN reserve for a long term basis, and that comes cheaper.


