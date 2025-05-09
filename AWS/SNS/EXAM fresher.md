**Configure an Amazon SNS topic to receive payment events from an AWS Lambda function. Set up multiple subscribers, such as Lambda functions, to process the events:** This is correct because SNS is a fully managed pub/sub messaging service that supports high-throughput, scalable delivery to multiple subscribers, which aligns with the company's requirements.

**Configure an Amazon EventBridge rule to capture payment events and route them to multiple AWS Lambda functions that handle downstream processing:** This is incorrect because EventBridge is more suited for complex event routing scenarios and not optimized for simple pub/sub use cases compared to SNS.

**Use Amazon Kinesis Data Firehose to deliver payment events to multiple S3 buckets. Configure downstream services to poll the buckets for event processing:** This is incorrect because Kinesis Data Firehose is designed for streaming data delivery, not for pub/sub messaging. It adds unnecessary overhead for the described use case.

**Use Amazon MQ as a message broker to enable publish/subscribe communication between the payment microservices and the downstream services:** This is incorrect because Amazon MQ is a managed message broker service that is typically used for legacy applications requiring protocols such as JMS or AMQP. It adds more operational complexity compared to SNS.

Question 65:

A fintech company is modernizing its payments processing system to adopt a serverless microservices architecture. The company wants to decouple its services and implement an event-driven architecture to support a publish/subscribe (pub/sub) model. The system needs to notify multiple downstream services when payment events occur, ensuring scalability and low operational overhead.

Which solution will meet these requirements MOST cost-effectively?