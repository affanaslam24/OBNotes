A financial institution is designing the architecture for a new data processing platform on AWS. The institution uses organizational units (OUs) in AWS Organizations to manage its accounts. To comply with regulatory requirements, all Amazon EC2 instances must include a compliance-level tag with values of compliant or noncompliant. IAM users must not be allowed to create EC2 instances without this tag or modify the tag after creation.

Which combination of steps will meet these requirements? (Select TWO.)


**In AWS Organizations, create a service control policy (SCP) to deny the creation of EC2 instances if the compliance-level tag is not specified. Attach the SCP to the appropriate OU:** This is correct because SCPs are used to enforce policies across accounts in an organization. By denying the creation of EC2 instances without the required tag, this SCP ensures that all instances are tagged at creation.

**In AWS Organizations, create a tag policy to enforce the use of the compliance-level tag with the required values. Attach the tag policy to the appropriate OU to ensure EC2 instances adhere to the tagging requirements:** This is correct because tag policies enforce tagging standards for AWS resources. By attaching the tag policy to the OU, you ensure that all EC2 instances follow the defined tagging requirements.

**Use AWS Config to check for compliance-level tags on EC2 instances. Configure AWS Config to remediate noncompliant resources by automatically adding the required tags to EC2 instances:** This is incorrect because AWS Config cannot prevent resource creation or modification. It can detect noncompliance but requires additional tools like Lambda for remediation, which introduces operational overhead.

**Create an IAM policy that denies the deletion of tags on EC2 instances. Assign this policy to all IAM users who manage EC2 resources in the organization's accounts:** This is incorrect because IAM policies apply only at the user or role level and cannot enforce organization-wide restrictions. SCPs and tag policies are better suited for this requirement.

**Use AWS Lambda with an EventBridge rule to trigger a function whenever a new EC2 instance is created. Configure the function to terminate any instance that does not include the compliance-level tag with the correct values:** This is incorrect because using Lambda for real-time remediation introduces operational complexity. SCPs and tag policies are more efficient and simpler to manage.



---


![[Pasted image 20250415195108.png]]


The easiest way to enforce this requirement is to update the password policy that applies to the entire AWS account. When you create or change a password policy, most of the password policy settings are enforced the next time your users change their passwords. However, some of the settings are enforced immediately such as the password expiration period.

**CORRECT:** "Set a password policy for the entire AWS account" is the correct answer.

**INCORRECT:** "Set a password policy for each IAM user in the AWS account" is incorrect. There’s no need to set an individual password policy for each user, it will be easier to set the policy for everyone.

**INCORRECT:** "Create an IAM policy that enforces the requirements and apply it to all users" is incorrect. As there is no specific targeting required it is easier to update the account password policy.

**INCORRECT:** "Use an AWS Config rule to enforce the requirements when creating user accounts" is incorrect. You cannot use AWS Config to enforce the password requirements at the time of creating a user account.

---

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Mystery Policy",
      "Action": [
        "ec2:RunInstances"
      ],
      "Effect": "Allow",
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "aws:RequestedRegion": "eu-west-1"
        }
      }
    }
```


**t allows running Amazon EC2 instances only in the `eu-west-1` region, and the API call can be made from anywhere in the world**

You manage access in AWS by creating policies and attaching them to IAM identities (users, groups of users, or roles) or AWS resources. A policy is an object in AWS that, when associated with an identity or resource, defines their permissions. AWS evaluates these policies when an IAM principal (user or role) makes a request. Permissions in the policies determine whether the request is allowed or denied. Most policies are stored in AWS as JSON documents. AWS supports six types of policies: identity-based policies, resource-based policies, permissions boundaries, Organizations service control policy (SCPs), access control lists (ACLs), and session policies.

You can use the `aws:RequestedRegion` key to compare the AWS Region that was called in the request with the Region that you specify in the policy. You can use this global condition key to control which Regions can be requested.

`aws:RequestedRegion` represents the target of the API call. So in this example, we can only launch an Amazon EC2 instance in `eu-west-1`, and we can do this API call from anywhere.

Incorrect options:

**It allows running Amazon EC2 instances anywhere but in the `eu-west-1` region**

**It allows running Amazon EC2 instances in any region when the API call is originating from the `eu-west-1` region**

**It allows running Amazon EC2 instances in the `eu-west-1` region, when the API call is made from the `eu-west-1` region**

These three options contradict the earlier details provided in the explanation. To summarize, `aws:RequestedRegion` represents the target of the API call. So, we can only launch an Amazon EC2 instance in `eu-west-1` region and we can do this API call from anywhere. Hence these options are incorrect.