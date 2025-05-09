- a very crucuiall product
![[Pasted image 20250410105642.png]]


![[Pasted image 20250410105736.png]]


![[Pasted image 20250410105832.png]]

- agent needs to be installed locally for transfering data and managing things in client side.
- it communicated over nfs or cmb
- it can recover from failures, can schedule at particular timings
- can throttle the bandwith and manage it accordingly as well.
- s3, efs, fsx



![[Pasted image 20250410110124.png]]


- when you need t o transfer a huge amount of data, traditional or whatwver, with great details.
- bandwith throttle,
- automatic recovery
- sscheduling
- compression and encryption.

but how is it different from other data migration services? search it  up



---


he most reliable and time-efficient solution that keeps the data secure is to use AWS DataSync and synchronize the data from the NAS device directly to Amazon S3. This should take place over an AWS Direct Connect connection to ensure reliability, speed, and security.

AWS DataSync can copy data between Network File System (NFS) shares, Server Message Block (SMB) shares, self-managed object storage, AWS Snowcone, Amazon Simple Storage Service (Amazon S3) buckets, Amazon Elastic File System (Amazon EFS) file systems, and Amazon FSx for Windows File Server file systems.

A company runs an application in an on-premises data center that collects environmental data from production machinery. The data consists of JSON files stored on network attached storage (NAS) and around 5 TB of data is collected each day. The company must upload this data to Amazon S3 where it can be processed by an analytics application. The data must be transferred securely.

Which solution offers the MOST reliable and time-efficient data transfer?


