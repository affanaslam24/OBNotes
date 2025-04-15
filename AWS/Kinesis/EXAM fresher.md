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