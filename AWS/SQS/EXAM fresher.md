
Amazon SQS offers buffer capabilities to smooth out temporary volume spikes without losing messages or increasing latency.

So it can be used for bufferring or throttle process.

Amazon **Kinesis Data Streams** is used to **collect, process, and analyze real-time, streaming data**. It’s ideal for scenarios where **data is generated continuously**, and you want to process or analyze it **as soon as it arrives**.

so with kinesis stream you have REAL TIME data interpretation, and SQS can be used for buffering and queing up the requests.


To prevent your API from being overwhelmed by too many requests, Amazon API Gateway throttles requests to your API using the token bucket algorithm, where a token counts for a request. Specifically, API Gateway sets a limit on a steady-state rate and a burst of request submissions against all APIs in your account. In the token bucket algorithm, the burst is the maximum bucket size.

Amazon Simple Queue Service (Amazon SQS) - Amazon Simple Queue Service (SQS) is a fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications. Amazon SQS offers buffer capabilities to smooth out temporary volume spikes without losing messages or increasing latency.

Amazon Kinesis - Amazon Kinesis is a fully managed, scalable service that can ingest, buffer, and process streaming data in real-time.


- **Load Balancer cannot throttle requests**



ALso, sns and sqs both can throttle data, but 
Amazon SQS has the ability to buffer its messages. Amazon Simple Notification Service (SNS) cannot buffer messages and is generally used with SQS to provide the buffering facility. When requests come in faster than your Lambda function can scale, or when your function is at maximum concurrency, additional requests fail as the Lambda throttles those requests with error code 429 status code. So, this combination of services is incorrect.



---
SNS and SQS together:
Imagine SNS as a **megaphone** announcing to the crowd (burst of messages), and SQS as the **line** outside a shop — only a few are let in at a time for service.

#### **SNS**:

- Broadcasts messages instantly (burst mode).
- Doesn’t wait — it just fires and forgets.
#### 🔸 **SQS**:
- Stores (buffers) the messages.
- Acts like a shock absorber — queues messages when traffic is high.
#### 🔸 **Consumer (App/Lambda/Worker)**:
- Pulls messages from SQS **at its own speed**.
- You can **control concurrency**, **limit read rates**, or use **batch processing**.

### Throttling Example:

Let’s say:
- You’re getting 1000 orders per second (via SNS).
- But your order processing app can only handle 100/sec.
✅ You subscribe an **SQS queue to SNS**.  
✅ Your worker app **polls SQS** and processes **100 msgs/sec**.  
✅ SQS holds the rest in a **buffer** and delivers slowly.

No messages are lost, and your system doesn’t crash due to overload.



- So try to remember, if you are trying to have a data with no data lost, but want to slow down or do throttle, then the services in mind would be:
	- sqs, sns
	- sqs, api gateway
	- NOT LOAD BALANCER


---


AWS Lambda lets you run code without provisioning or managing servers. You pay only for the compute time you consume. Amazon Simple Queue Service (SQS) is a fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications. SQS offers two types of message queues. Standard queues offer maximum throughput, best-effort ordering, and at-least-once delivery. SQS FIFO queues are designed to guarantee that messages are processed exactly once, in the exact order that they are sent.

AWS manages all ongoing operations and underlying infrastructure needed to provide a highly available and scalable message queuing service. With SQS, there is no upfront cost, no need to acquire, install, and configure messaging software, and no time-consuming build-out and maintenance of supporting infrastructure. SQS queues are dynamically created and scale automatically so you can build and grow applications quickly and efficiently.


---


![[Extra features]]



---

whenevr kinesis and sqs is used together, remenber that kinesis wins for real time features


---


![[Pasted image 20250415185313.png]]


i couldnt understand this at all:


FIFO queues preserve the order of messages but they do not prioritize messages within the queue. The orders would need to be placed into the queue in a priority order and there’s no way of doing this as the messages are sent automatically through event notifications as they are received by Amazon S3.


Batching adds efficiency but it has nothing to do with ordering or priority.

Short polling and long polling are used to control the amount of time the consumer process waits before closing the API call and trying again. Polling should be configured for efficiency of API calls and processing of messages but does not help with message prioritization.

AWS recommend using separate queues when you need to provide prioritization of work. The logic can then be implemented at the application layer to prioritize the queue for the paid photos over the queue for the free photos.

**CORRECT:** "Use a separate SQS Standard queue for each tier. Configure Amazon EC2 instances to prioritize polling for the paid queue over the free queue" is the correct answer.


A VERY IMPORTANT QUESTION. NEED TO UNDERSTAND THE DIFFERENT USE CASES.

---

**Use two Amazon Simple Queue Service (Amazon SQS) queues: one for data ingestion and one for route analysis. Configure the EC2 instances to poll their respective queues and scale the Auto Scaling groups based on the ApproximateNumberOfMessages metric in each queue:** This is correct because SQS decouples the ingestion and analysis processes, ensuring no data is lost during traffic spikes. Scaling the Auto Scaling groups based on the queue length allows for efficient scaling that matches the workload demand for each process.