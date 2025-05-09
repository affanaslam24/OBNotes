![[Pasted image 20250409230304.png]]

- think of extension, backup and mogration.


three modes:
![[Pasted image 20250409230439.png]]
didnt understand shit

![[Pasted image 20250416112027.png]]
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
- where you need local speed to frequently access data\



---


"AWS Storage Gateway" is incorrect as this service is primarily used for connecting on-premises storage to cloud storage. It consists of a software device installed on-premises and can be used with SMB shares but it actually stores the data on S3. It is also used for migration. However, in this case the company need to replace the file server farm and Amazon FSx is the best choice for this job.


The file gateway will then store data on Amazon S3 and has a local cache for data that can be accessed at low latency. The file gateway provides an excellent method of enabling file protocol access to low cost S3 object storage.


gile storage uses s3 as its location place.