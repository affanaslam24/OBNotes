**Use Amazon S3 Transfer Acceleration (Amazon S3TA) to enable faster file uploads into the destination S3 bucket**

Amazon S3 Transfer Acceleration enables fast, easy, and secure transfers of files over long distances between your client and an S3 bucket. Amazon S3TA takes advantage of Amazon CloudFront’s globally distributed edge locations. As the data arrives at an edge location, data is routed to Amazon S3 over an optimized network path.



**The junior scientist does not need to pay any transfer charges for the image upload**

There are no S3 data transfer charges when data is transferred in from the internet. Also with S3TA, you pay only for transfers that are accelerated. Therefore the junior scientist does not need to pay any transfer charges for the image upload because S3TA did not result in an accelerated transfer.

![[Pasted image 20250413201012.png]]

---

when to use Accelaration

A company operates a globally accessed video-sharing platform where users can upload, view, and download videos from their mobile devices. The platform's static website is hosted in an Amazon S3 bucket.

Due to the platform’s rapid growth, users are experiencing increased latency during video uploads and downloads. The company needs to improve the performance of the platform while minimizing the complexity of the implementation.

Which solution will meet these requirements with the LEAST implementation effort?


**Configure an Amazon CloudFront distribution for the S3 bucket to accelerate download performance. Enable S3 Transfer Acceleration to enhance upload performance:** This is correct because Amazon CloudFront is a global content delivery network (CDN) that improves download performance by caching content closer to users. S3 Transfer Acceleration reduces upload latency by utilizing optimized AWS edge locations to accelerate the data transfer from the user to the S3 bucket. Together, these services provide a cost-effective and low-effort solution to improve the platform's performance.

**Deploy Amazon EC2 instances in multiple AWS Regions and migrate the platform to these instances. Use an Application Load Balancer to distribute traffic across the instances and configure AWS Global Accelerator for improved global performance:** This is incorrect because migrating the platform to EC2 instances and configuring Global Accelerator is significantly more complex and requires ongoing maintenance. This solution involves more implementation effort compared to using managed AWS services like CloudFront and S3 Transfer Acceleration.

**Configure an Amazon CloudFront distribution with the S3 bucket as the origin to accelerate downloads. Use CloudFront for uploads as well. Create additional S3 buckets in multiple Regions and set up replication rules to sync user content between buckets. Redirect users to the closest bucket for downloads:** This is incorrect because adding multiple S3 buckets and setting up replication rules increases the complexity of the solution. While CloudFront can accelerate uploads and downloads, replicating buckets adds unnecessary operational overhead when S3 Transfer Acceleration can address upload latency more efficiently.

**Set up AWS Global Accelerator for the S3 bucket to optimize network routing. Configure the platform to use the Global Accelerator endpoint instead of the S3 bucket:** This is incorrect because AWS Global Accelerator does not directly support S3 buckets as an endpoint. Configuring Global Accelerator would require additional infrastructure, such as custom endpoints, increasing the effort and complexity without directly solving the latency issues.




See, we need no bring the network closer to us, tahts what we do with global accelaraton. it increases transfer and brings network closer.\

We need to make the data more accesible immediately, caching is required, and trnasfer of data, data upload needs to be quick to the S3.

**Also, Global accelratior doesnt uses S3.**



