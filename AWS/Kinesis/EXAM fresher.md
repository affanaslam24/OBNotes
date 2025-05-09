- So kinesis Data analytics is real time analysis.
- BU for that it needs to have the data being streamed into it.
- For the question, we used API gateways, why? because it has REST APIs as well as WEBSOCKET Apis that can perform real time data transmission.
- RedShift is a data warehouse, it stroes data, and can perform trends on it, but can really analyse and push it to give an output to a different service like KINESIS data analytics do.
- Athena can be used for queriying the data, not anaylise it for a real time computation. and S3 as its origin cannot be updated while its using it.
- Also, S3 doesnt has REST apis.
- TRICKY one is lambda. using api gateway to connect to Lambda, you think you can dop the compute for analysis, but the deal is, LAmbda has a time duration for computing, and it cannot store huge data. And here, we need huge data for analysis.


You can use Kinesis Data Analytics to transform and analyze streaming data in real-time with Apache Flink. Kinesis Data Analytics enables you to quickly build end-to-end stream processing applications for log analytics, clickstream analytics, Internet of Things (IoT), ad tech, gaming, etc. The four most common use cases are streaming extract-transform-load (ETL), continuous metric generation, responsive real-time analytics, and interactive querying of data streams. Kinesis Data Analytics for Apache Flink applications provides your application 50 GB of running application storage per Kinesis Processing Unit (KPU).

Amazon API Gateway is a fully managed service that allows you to publish, maintain, monitor, and secure APIs at any scale. Amazon API Gateway offers two options to create RESTful APIs, HTTP APIs and REST APIs, as well as an option to create WebSocket APIs.


![[Pasted image 20250413102554.png]]


---


- It is a fully managed service that automatically scales to match the throughput of your data and requires no ongoing administration. this is firehose.
- FIREHOSE IS SERVERLESS, it can output and input data however you want.
- **Kinesis Data Streams cannot directly write the output to Amazon S3.**
- ALso, kinesis data firehose is inbuilt to use with lambda for filter, thats its feature.
- Kinesis Data Analytics cannot directly ingest data from the source as it ingests data either from Kinesis Data Streams or Kinesis Data Firehose. So kinesis cant take data from other sources apart from data stream or firehose


Firehose cannot directly write into a DynamoDB table, so this option is incorrect.


---


1. Routing related records to the same record processor (as in streaming MapReduce). For example, counting and aggregation are simpler when all records for a given key are routed to the same record processor.
2. Ordering of records. For example, you want to transfer log data from the application host to the processing/archival host while maintaining the order of log statements.
3. Ability for multiple applications to consume the same stream concurrently. For example, you have one application that updates a real-time dashboard and another that archives data to Amazon Redshift. You want both applications to consume data from the same stream concurrently and independently.
4. Ability to consume records in the same order a few hours later. For example, you have a billing application and an audit application that runs a few hours behind the billing application. Because Amazon Kinesis Data Streams stores data for up to 365 days, you can run the audit application up to 365 days behind the billing application.

---

KDS provides ordering of records, as well as the ability to read and/or replay records in the same order to multiple Amazon Kinesis Applications.

---


Amazon Kinesis Data Streams collect and process data in real time. A _Kinesis data stream_ is a set of [shards](https://docs.aws.amazon.com/streams/latest/dev/key-concepts.html#shard). Each shard has a sequence of data records. Each data record has a [sequence number](https://docs.aws.amazon.com/streams/latest/dev/key-concepts.html#sequence-number) that is assigned by Kinesis Data Streams. A _shard_ is a uniquely identified sequence of data records in a stream.

A _partition key_ is used to group data by shard within a stream. Kinesis Data Streams segregates the data records belonging to a stream into multiple shards. It uses the partition key that is associated with each data record to determine which shard a given data record belongs to.
![](https://img-c.udemycdn.com/redactor/raw/2020-05-21_01-04-57-65202de89627ab9ac70ef6b89817c981.jpg)


"Use Amazon Kinesis Data Streams for real-time events with a shard for each device. Use Amazon Kinesis Data Firehose to save data to Amazon EBS" is incorrect as you cannot save data to EBS from Kinesis.

---

"Use an Amazon SQS standard queue for real-time events with one queue for each device. Trigger an AWS Lambda function from the SQS queue to save data to Amazon S3" is incorrect as SQS is not the most efficient service for streaming, real time data.

---


A company provides a REST-based interface to an application that allows a partner company to send data in near-real time. The application then processes the data that is received and stores it for later analysis. The application runs on Amazon EC2 instances.

The partner company has received many 503 Service Unavailable Errors when sending data to the application and the compute capacity reaches its limits and is unable to process requests when spikes in data volume occur.

Which design should a Solutions Architect implement to improve scalability?

-
- kinesis stream for huge real time data, (coyudlve used sqs but we specifically said real time need)
- lambda for scalability, also if youre worried about the store option, Lambda can store it to S3 or other places after each compute.

---

A financial services company wants a single log processing model for all the log files (consisting of system logs, application logs, database logs, etc) that can be processed in a serverless fashion and then durably stored for downstream analytics. The company wants to use an AWS managed service that automatically scales to match the throughput of the log data and requires no ongoing administration. As a solutions architect, which of the following AWS services would you recommend solving this problem?


Keywords:
all log files
no administration
automatic scales
serverless
**durably stored**


Kinesis firehose!!!

- **Serverless**: No need to manage infrastructure.
- **Fully managed**: No ongoing administration.
- **Auto-scales**: Matches log data throughput automatically.
- **Durable storage**: Can deliver logs to **Amazon S3**, **Amazon Redshift**, **Amazon OpenSearch**, or a custom HTTP endpoint.
- **Near real-time processing**: Supports data transformation using **AWS Lambda** before storage.
- **Supports various log types**: Works well for system, app, and DB logs from multiple sources 

