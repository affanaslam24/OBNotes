	![[Pasted image 20250408214647.png]]
- near real time
- can transform the data using lambda on hte fly, but takes time
- billed based on the volume pf data being passed thorugh it.
- remember, used for data analytics, data storing, and data lakes.



### Details
![[Pasted image 20250408220108.png]]

- first, always remeber its used to store Persistent data stream, which the usual kinesis stream cant do.
- NOw, rememebe rthe consumers- http, splunk, redshift, elaticsearch, S3 buckets.
- its producers? it can be the kinesis stream itself, or the production group directly.
- In either case we have a near real time buffer of data passing through it.
- kinesis stream has real time passing, but even still the kinesis firehose tkes it time.
- buffer time is 60 seconds, or 1 MB of data stored and readyv to send.
- it can be processed and channged into different data before sending as well, using lambda, **BUT its not real time**.
- **If you want real time data modification, you can use Kinesis stream to chang the data and then use other services.**
- Before sending the data to lambda from Firehose, one can send the **original data** to S3 buckets as well as backuop data.

- All the data are direct end to end transmission from the kinesis firehose to the consumer, but in redshift there is an intermediatery s3 bucket which copies the data. Even still, the data is then taken from S3 to the redshit thorough firehose (i guess, not sure). Sure, that there is an intermediatery tho.



- Firehose cannot directly write into a DynamoDB table, so this option is incorrect.
- It is a fully managed service that automatically scales to match the throughput of your data and requires no ongoing administration
- It can also batch, compress, transform, and encrypt the data before loading it, minimizing the amount of storage used at the destination and increasing security.
- IT can have only kinesis data stream at its producer, or a bunch of other devices, but not both at the same time.
- 


---


An IT company is working on client engagement to build a real-time data analytics tool for the Internet of Things (IoT) data. The IoT data is funneled into Amazon Kinesis Data Streams which further acts as the source of a delivery stream for Amazon Kinesis Firehose. The engineering team has now configured a Kinesis Agent to send IoT data from another set of devices to the same Amazon Kinesis Firehose delivery stream. They noticed that data is not reaching Kinesis Firehose as expected. As a solutions architect, which of the following options would you attribute as the MOST plausible root cause behind this issue?


**Kinesis Agent cannot write to Amazon Kinesis Firehose for which the delivery stream source is already set as Amazon Kinesis Data Streams**

Amazon Kinesis Data Firehose is the easiest way to reliably load streaming data into data lakes, data stores, and analytics tools. It is a fully managed service that automatically scales to match the throughput of your data and requires no ongoing administration. It can also batch, compress, transform, and encrypt the data before loading it, minimizing the amount of storage used at the destination and increasing security. When an Amazon Kinesis Data Stream is configured as the source of a Kinesis Firehose delivery stream, Firehose’s `PutRecord` and `PutRecordBatch` operations are disabled and Kinesis Agent cannot write to Kinesis Firehose Delivery Stream directly. Data needs to be added to the Amazon Kinesis Data Stream through the Kinesis Data Streams `PutRecord` and `PutRecords` operations instead. Therefore, this option is correct.

Incorrect options:

**Kinesis Agent can only write to Amazon Kinesis Data Streams, not to Amazon Kinesis Firehose** - Kinesis Agent is a stand-alone Java software application that offers an easy way to collect and send data to Amazon Kinesis Data Streams or Amazon Kinesis Firehose. So this option is incorrect.

**Amazon Kinesis Firehose delivery stream has reached its limit and needs to be scaled manually** - Amazon Kinesis Firehose is a fully managed service that automatically scales to match the throughput of your data and requires no ongoing administration. Therefore this option is not correct.

How Amazon Kinesis Firehose works:

![](https://d1.awsstatic.com/Products/product-name/diagrams/product-page-diagram_Amazon-Kinesis-Data-Firehose.9340b812ab86518341c47b24316995b3792bf6e1.png)

via - [https://aws.amazon.com/kinesis/data-firehose/](https://aws.amazon.com/kinesis/data-firehose/)

**The data sent by Kinesis Agent is lost because of a configuration error** - This is a made-up option and has been added as a distractor.