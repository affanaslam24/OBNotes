This solution ensures that the same open-source software is used for automating the deployment, scaling, and management of containerized applications both on-premises and in the AWS Cloud.

![](https://img-c.udemycdn.com/redactor/raw/test_question_description/2020-11-27_09-55-33-2abdd31ee10dd8c28e19ec75e2a29309.jpg)


so what we know is, when the application has same software config, we use EKS and not ECS

Questoin was:
A company runs containerized applications for many application workloads in an on-premise data center. The company is planning to deploy containers to AWS and the chief architect has mandated that the same configuration and administrative tools must be used across all containerized environments. The company also wishes to remain cloud agnostic to safeguard against the impact of future changes in cloud strategy.


---


**Create separate IAM roles with policies for Amazon S3 and DynamoDB access. Use Kubernetes service accounts with IAM Role for Service Accounts (IRSA) to assign the AmazonS3FullAccess policy to the reporting service Pods and the AmazonDynamoDBFullAccess policy to the management dashboard Pods:** This is correct because IAM Role for Service Accounts (IRSA) allows the assignment of IAM roles directly to Kubernetes service accounts, which the Pods use to assume permissions. This solution enables fine-grained access control, ensuring that the Pods for the management dashboard can access only DynamoDB and the Pods for the reporting service can access only S3.