- in SSE-S3, aws maanges the keys for your. it encrypts and decrypts, but you dont have access to the key. it rorates regularly and everything as well
- in SSSE-KMS, the key is generated in KMS, and since KMS is a managed key service, there will be an sudit trail as well well who can use it, and who used it, these details will be stored.
- in SSE-C youp provide the key, S# encrypts and decrypts the data. Amazon S3 manages the encryption, as it writes to disks, and decryption when you access your objects.

---

Following are the unsupported life cycle transitions for S3 storage classes - Any storage class to the Amazon S3 Standard storage class. Any storage class to the Reduced Redundancy storage class. The Amazon S3 Intelligent-Tiering storage class to the Amazon S3 Standard-IA storage class. The Amazon S3 One Zone-IA storage class to the Amazon S3 Standard-IA or Amazon S3 Intelligent-Tiering storage classes.

Here are the supported life cycle transitions for S3 storage classes - The S3 Standard storage class to any other storage class. Any storage class to the S3 Glacier or S3 Glacier Deep Archive storage classes. The S3 Standard-IA storage class to the S3 Intelligent-Tiering or S3 One Zone-IA storage classes. The S3 Intelligent-Tiering storage class to the S3 One Zone-IA storage class. The S3 Glacier storage class to the S3 Glacier Deep Archive storage class.

![[Pasted image 20250413145512.png]]

---

A file-hosting service uses Amazon Simple Storage Service (Amazon S3) under the hood to power its storage offerings. Currently all the customer files are uploaded directly under a single Amazon S3 bucket. The engineering team has started seeing scalability issues where customer file uploads have started failing during the peak access hours with more than 5000 requests per second.

Which of the following is the MOST resource efficient and cost-optimal way of addressing this issue?


**or example, your application can achieve at least 3,500 PUT/COPY/POST/DELETE or 5,500 GET/HEAD requests per second per prefix in a bucket.**


There are no limits to the number of prefixes in a bucket. You can increase your read or write performance by parallelizing reads. For example, if you create 10 prefixes in an Amazon S3 bucket to parallelize reads, you could scale your read performance to 55,000 read requests per second. Please see this example for more clarity on prefixes: if you have a file f1 stored in an S3 object path like so `s3://your_bucket_name/folder1/sub_folder_1/f1`, then `/folder1/sub_folder_1/` becomes the prefix for file f1.

Some data lake applications on Amazon S3 scan millions or billions of objects for queries that run over petabytes of data. These data lake applications achieve single-instance transfer rates that maximize the network interface used for their Amazon EC2 instance, which can be up to 100 Gb/s on a single instance. These applications then aggregate throughput across multiple instances to get multiple terabits per second. Therefore creating customer-specific custom prefixes within the single bucket and then uploading the daily files into those prefixed locations is the BEST solution for the given constraints.


---
![[S3 Accelarated transfer]]

---

Multipart upload allows you to upload a single object as a set of parts. Each part is a contiguous portion of the object's data. You can upload these object parts independently and in any order. If transmission of any part fails, you can retransmit that part without affecting other parts. After all parts of your object are uploaded, Amazon S3 assembles these parts and creates the object. In general, when your object size reaches 100 MB, you should consider using multipart uploads instead of uploading the object in a single operation. Multipart upload provides improved throughput, therefore it facilitates faster file uploads.

 If you're uploading large objects over a stable high-bandwidth network, use multipart uploading to maximize the use of your available bandwidth by uploading object parts in parallel for multi-threaded performance. If you're uploading over a spotty network, use multipart uploading to increase resiliency to network errors by avoiding upload restarts.


ALSO, you can use Accelarated transfer as well as multipart both at the same time.


---

**Upload the compressed file in a single operation** - In general, when your object size reaches 100 megabytes, you should consider using multipart uploads instead of uploading the object in a single operation. Multipart upload provides improved throughput - you can upload parts in parallel to improve throughput. Therefore, this option is not correct.


**Upload the compressed file using multipart upload** - Although using multipart upload would certainly speed up the process, combining with Amazon S3 Transfer Acceleration (Amazon S3TA) would further improve the transfer speed. Therefore just using multipart upload is not the correct option.


---

there is a minimum day duration of 30 days in one zone IA of S3.

![[Pasted image 20250413190702.png]]

A media agency stores its re-creatable assets on Amazon Simple Storage Service (Amazon S3) buckets. The assets are accessed by a large number of users for the first few days and the frequency of access falls down drastically after a week. Although the assets would be accessed occasionally after the first week, but they must continue to be immediately accessible when required. The cost of maintaining all the assets on Amazon S3 storage is turning out to be very expensive and the agency is looking at reducing costs as much as possible.

The keyword in this question was: "**Re-Creatable**"
Means, we only needed one zpne IA, because the replication and high availibility wouldve been provided by the agency itself.


---


**The junior scientist does not need to pay any transfer charges for the image upload**

There are no S3 data transfer charges when data is transferred in from the internet. Also with S3TA, you pay only for transfers that are accelerated. Therefore the junior scientist does not need to pay any transfer charges for the image upload because S3TA did not result in an accelerated transfer.

So this is crazy, S3 accelation


---

There are no S3 data transfer charges when data is transferred in from the internet.

---

S3 IA one zone vs Intelligent tier

Q.An audit department generates and accesses the audit reports only twice in a financial year. The department uses AWS Step Functions to orchestrate the report creating process that has failover and retry scenarios built into the solution. The underlying data to create these audit reports is stored on Amazon S3, runs into hundreds of Terabytes and should be available with millisecond latency.

As an AWS Certified Solutions Architect – Associate, which is the MOST cost-effective storage class that you would recommend to be used for this use-case?


- keyword, one year, 2 times. 
- retry scenarios

**Amazon S3 Intelligent-Tiering (S3 Intelligent-Tiering)** - For a small monthly object monitoring and automation charge, Amazon S3 Intelligent-Tiering monitors access patterns and automatically moves objects that have not been accessed to lower-cost access tiers. The Amazon S3 Intelligent-Tiering storage class is designed to optimize costs by automatically moving data to the most cost-effective access tier, without performance impact or operational overhead. S3 Standard-IA matches the high durability, high throughput, and low latency of S3 Intelligent-Tiering, with a low per GB storage price and per GB retrieval fee. Moreover, Standard-IA has the same availability as that of Amazon S3 Intelligent-Tiering. So, it's cost-efficient to use S3 Standard-IA instead of S3 Intelligent-Tiering.

- notice that IA one zone has less price compared to idle intelligent pairing.
- IA one zone provides the same availibility


Since the data is accessed only twice in a financial year but needs rapid access when required, the most cost-effective storage class for this use-case is Amazon S3 Standard-IA. S3 Standard-IA storage class is for data that is accessed less frequently but requires rapid access when needed. S3 Standard-IA matches the high durability, high throughput, and low latency of S3 Standard, with a low per GB storage price and per GB retrieval fee. Amazon Standard-IA is designed for 99.9% availability compared to 99.99% availability of Amazon S3 Standard. However, the report creation process has failover and retry scenarios built into the workflow, so in case the data is not available owing to the 99.9% availability of Amazon S3 Standard-IA, the job will be auto re-invoked till data is successfully retrieved. Therefore this is the correct option.


---


**Enable multi-factor authentication (MFA) delete on the Amazon S3 bucket**

To provide additional protection, multi-factor authentication (MFA) delete can be enabled. MFA delete requires secondary authentication to take place before objects can be permanently deleted from an Amazon S3 bucket. Hence, this is the correct option.

---

also, versioning enables security towards misrtaken deleting of the files by putting a delete marker in the versioned delte object.