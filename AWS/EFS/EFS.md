problem without efs

![[Pasted image 20250402151114.png]]


NFS= network file system
we use nfsv4 for efs

![[Pasted image 20250402163358.png]]


## Its Architecture
![[Pasted image 20250402163623.png]]

So **it can only be used isnide a vpc**, and can be distributed between various AZs. But for that you need to configure as many mount targets inside AZs as possible, for high availibility, like how we do it in NAT gateways.

EC2 and other products that want to access this EFS will need to access the mount target.



## Its functionalities
![[Pasted image 20250402164547.png]]
So, as you can see, most of these are common to ec2 and S3 functionalities, and i think we need to learn these commonalities properly.

Standard and infrequent access in EC2. which are classes inside EC2
General purpose and Max IO in EBS.
Burstring and provisoned modes in EBS
Lifecycle Policies in S3.


can use KMS 



