We need to document a lot of things on how the organisation is being used.
Bit lets talk about SCP
![[Screenshot from 2025-03-29 14-39-49.png]]

they dont grant permissions, they limit the permissions.

remember the name.
![[Screenshot from 2025-03-29 14-42-05.png]]

in case of identity policy in accounts and scp both, only the commonities will be adressed.

**But the crucial point is, what are these identity policies? are they attached to the users or roles? check this one.**



To apply the restrictions across multiple member accounts you must use a Service Control Policy (SCP) in the AWS Organization. The way you would do this is to create a deny rule that applies to anything that does not equal the specific instance type you want to allow.

The following architecture could be used to achieve this goal:

![](https://img-c.udemycdn.com/redactor/raw/2020-05-21_00-48-06-e73551726ea3baf15e8e687947948cba.jpg)

---


Different accounts in organisation

You would like to migrate an AWS account from an AWS Organization A to an AWS Organization B. What are the steps do to it?

**Remove the member account from the old organization. Send an invite to the member account from the new Organization. Accept the invite to the new organization from the member account**

AWS Organizations helps you centrally govern your environment as you grow and scale your workloads on AWS. Using AWS Organizations, you can automate account creation, create groups of accounts to reflect your business needs, and apply policies for these groups for governance. You can also simplify billing by setting up a single payment method for all of your AWS accounts. Through integrations with other AWS services, you can use Organizations to define central configurations and resource sharing across accounts in your organization.

To migrate accounts from one organization to another, you must have root or IAM access to both the member and master accounts. Here are the steps to follow: 1. Remove the member account from the old organization 2. Send an invite to the member account from the new Organization 3. Accept the invite to the new organization from the member account


