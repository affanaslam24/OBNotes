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

