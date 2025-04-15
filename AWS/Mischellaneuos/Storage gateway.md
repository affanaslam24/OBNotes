![[Pasted image 20250409230304.png]]

- think of extension, backup and mogration.


three modes:
![[Pasted image 20250409230439.png]]
didnt understand shit


![[Pasted image 20250409230606.png]]
- stores as files
- for extesnion or migratiob

![[Pasted image 20250409230727.png]]
- when an existing backup is thre and you want ot move it to aws.
- it can store a huge amount of those backup dats. mograting this data.


![[Pasted image 20250409230941.png]]
- gateway stored are like blocks or EBS like
- they are for migration and disaster recovery.
- its asynchronos, that means it wokrs in backgtounf wihtout affectingthe workload. its like Ebs volume created in background.
- heere primary data is cached on prem and the aws creates EBS snapshots of it


![[Pasted image 20250409231503.png]]
- when you want to extend your storage.
- primary data is cached in S3 volume, AWS managed buckets snalpots.
- Similar to file storage type, but here we use S3 and ebs
- where you need local speed to frequently access data