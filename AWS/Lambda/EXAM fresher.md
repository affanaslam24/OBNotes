![[Pasted image 20250413200552.png]]

Lambda can only work with 1000 concurrent executions

![[Pasted image 20250413200631.png]]


**Amazon SNS has hit a scalability limit, so the team needs to contact AWS support to raise the account limit** - Amazon SNS leverages the proven AWS cloud to dynamically scale with your application. You don't need to contact AWS support, as SNS is a fully managed service, taking care of the heavy lifting related to capacity planning, provisioning, monitoring, and patching. Therefore, this option is incorrect


----

 IMportant
 :
 As both AWS Lambda and Amazon SNS are serverless and fully managed services, the engineering team cannot provision more servers

---


Websocket apis are stateful
restApi are stateless
Http is stateless


---

A media processing company is migrating its on-premises application to the AWS Cloud. The application processes high volumes of videos and generates large output files during the workflow.

The company requires a scalable solution to handle an increasing number of video processing jobs. The solution should minimize manual intervention, simplify job orchestration, and eliminate the need to manage infrastructure. Operational overhead must be kept to a minimum.

Which solution will fulfill these requirements with the LEAST operational overhead?

**Use AWS Batch to run video processing jobs. Use AWS Step Functions to manage the workflow. Store the processed files in Amazon S3:** This is correct because AWS Batch automatically manages the underlying infrastructure, scales based on workload and simplifies batch job management. Combining this with AWS Step Functions enables efficient orchestration of workflows. Storing the processed files in Amazon S3 provides durability and scalability, which is ideal for managing large files. This solution minimizes operational overhead by leveraging fully managed services.

**Use Amazon Elastic Container Service (Amazon ECS) with AWS Fargate to process the videos. Use Amazon Simple Queue Service (Amazon SQS) for workflow orchestration and store the processed files in Amazon S3:** This is incorrect because, while Fargate reduces infrastructure management, integrating SQS for workflow orchestration adds complexity compared to using AWS Step Functions. AWS Batch provides more specialized functionality for processing batch workloads.



---


- An ASG cannot launch instances in multiple Regions.
- If you want high Availibility, you need to make it in two Azs.
- Being in same subnet could mean the subnets are in the same AZ, which could be risky.
---

