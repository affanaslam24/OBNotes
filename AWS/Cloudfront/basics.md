![[Pasted image 20250413183548.png]]


![[Pasted image 20250409110537.png]]
- always remeber, cloudfront is used for caching your origin data.
- **it doesnt brings the netwrok closer**

![[Pasted image 20250409110757.png]]
Well learn about the terminology later:
- origin is the location where the content is stored.
- we will know of 2 origin types:
	- S3 origin- objects stored in S3
	- custom- anything else apart from S3 origin. Infact , s3 with static website is custom origin. And this is a crucial difference.
- Distribution is what configures cloudfront, the settings, policies, OAI connection etc of the cloudfront.
- IMPORTANT- configuration unit is inside distribution of cloudfront.
- there is edge location and then the larger version of it.

![[Screenshot from 2025-04-09 11-12-13.png]]
- so we know that distribution is where the configuration is stored.
- distribution is what provides us with a DNS name, and we can use **Alternative dommain name** to point this Dns name to a provided Domain name of ours
- Now, for S3 origin, or for S3 static hosting, we dont need custom SSl certificate, but for others we need to provide ACM certificate.
- IMPORTANT- for any reading, we have caching, but for writing anything to the origin, it would be done directly.







- how does the certification work in cloudfront?