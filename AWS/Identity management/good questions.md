![[Pasted image 20250415233243.png]]

---

![[Pasted image 20250416152705.png]]



With IAM roles for Amazon ECS tasks, you can specify an IAM role that can be used by the containers in a task. Applications must sign their AWS API requests with AWS credentials, and this feature provides a strategy for managing credentials for your applications to use, similar to the way that Amazon EC2 instance profiles provide credentials to EC2 instances.

You define the IAM role to use in your task definitions, or you can use a taskRoleArn override when running a task manually with the RunTask API operation.

Note that there are instances roles and task roles that you can assign in ECS when using the EC2 launch type. The task role is better when you need to assign permissions for just that specific task:

![](https://img-c.udemycdn.com/redactor/raw/test_question_description/2021-02-25_12-02-13-cca043ef28407cf8376847f12e461e32.jpg)

**CORRECT:** "Create an IAM role that has read/write permissions to the bucket and update the task definition to specify the role as the taskRoleArn" is the correct answer.

**INCORRECT:** "Update the S3 policy in IAM to allow read/write access from Amazon ECS, and then relaunch the container" is incorrect. Policies must be assigned to tasks using IAM Roles and this is not mentioned here.

**INCORRECT:** "Create a set of Access Keys with read/write permissions to the bucket and update the task credential ID" is incorrect. You cannot update the task credential ID with access keys and roles should be used instead.

**INCORRECT:** "Attach an IAM policy with read/write permissions to the bucket to an IAM group and add the container instances to the group" is incorrect. You cannot add container instances to an IAM group.

