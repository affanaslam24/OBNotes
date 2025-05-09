**NEW SERVICE:**
**IAM PERMISSION boundary:**
**Use permissions boundary to control the maximum permissions employees can grant to the IAM principals**

A permissions boundary can be used to control the maximum permissions employees can grant to the IAM principals (that is, users and roles) that they create and manage. As the IAM administrator, you can define one or more permissions boundaries using managed policies and allow your employee to create a principal with this boundary. The employee can then attach a permissions policy to this principal. However, the effective permissions of the principal are the intersection of the permissions boundary and permissions policy. As a result, the new principal cannot exceed the boundary that you defined. Therefore, using the permissions boundary offers the right solution for this use-case.
![[Pasted image 20250413134118.png]]

- also, for databases, you cant remove permissions for all users, because some users need administer level authority.
- Simialry, and this is IMPORTANT, that you dont use your root admin for works.


An **IAM Principal** is **any identity that can make a request to AWS services**.

#### Examples of IAM Principals:

- **IAM user** — e.g., `Alice`, an admin in your account.
- **IAM role** — e.g., a Lambda function assuming a role to access S3.
- **Federated user** — e.g., someone logging in via an identity provider like Google or Okta.
💡 Think of it as: "**Who is making the request?**"


So its not a new service, but a new way of terminology.


A **Permissions Boundary** is an _advanced security control_ that acts like a **maximum permissions limit** for an IAM role or user.
##### How it works:
Even if a user or role has an IAM policy that allows certain actions, the permissions boundary can **further restrict** what they’re allowed to do.
🧠 It’s like:
> "Even if your policy allows `s3:*`, the boundary will only allow `s3:GetObject`. So that’s the max you can do."

---

AWS supports permissions boundaries for IAM entities (users or roles). A permissions boundary is an advanced feature for using a managed policy to set the maximum permissions that an identity-based policy can grant to an IAM entity. An entity's permissions boundary allows it to perform only the actions that are allowed by both its identity-based policies and its permissions boundaries. Here we have to use an IAM permission boundary. They can only be applied to roles or users, not IAM groups.

Permissions boundaries for IAM entities:

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q39-i1.jpg)

via - [https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_boundaries.html)

Incorrect options:

**Create a Service Control Policy (SCP) on your AWS account that restricts developers from attaching themselves the `AdministratorAccess` policy** - Service control policy (SCP) is one type of policy that you can use to manage your organization. SCPs offer central control over the maximum available permissions for all accounts in your organization, allowing you to ensure your accounts stay within your organization’s access control guidelines. SCPs are available only in an organization that has all features enabled. SCPs aren't available if your organization has enabled only the consolidated billing features. Attaching an SCP to an AWS Organizations entity (root, OU, or account) defines a guardrail for what actions the principals can perform. If you consider this option, since AWS Organizations is not mentioned in this question, so we can't apply an SCP.

**Attach an IAM policy to your developers, that prevents them from attaching the `AdministratorAccess` policy** - This option is incorrect as the developers can remove this policy from themselves and escalate their privileges.

**Put the developers into an IAM group, and then define an IAM permission boundary on the group that will restrict the managed policies they can attach to themselves** - IAM permission boundary can only be applied to roles or users, not IAM groups. Hence this option is incorrect.

References: