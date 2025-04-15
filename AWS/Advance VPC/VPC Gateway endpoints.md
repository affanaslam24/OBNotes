
- created per service per region
- you create a gateway endpoint for S3 in one region, like US-east-1.
- asnd then attach it to mor than one subnet of a vpc.
- it doesnt goes inside any subnet
- - can specify which buckets it can access to
- its a logical gateway object which can only be accessed through inside a vpc
![[Pasted image 20250409185935.png]]

- so how it works is, its inside a vpc, not any particular Subnet.
- Can be added to more than one Subnet.
- Can be associated to subnet, and automatically a **prefix list** is added in the **route table**.
- prefix list is a logical representation of the endpoint
- Cant be cross region.

Extra security:
- for a private Bucket, what you can do is just add gateway endpoint in its policy, andit will  be done?



---
![[Screenshot from 2025-04-09 19-00-53.png]]
This is the arch of without endpoint.
- public instances need to access thorighb the IGW, and the routing hapens through route table.
- private subnets also sent the traffic to route table, route table sends it to nat gateqay and the nat gateway then sends back to route table and then goes to internet gsteway then to the service.

---
with endpoint:

![[Screenshot from 2025-04-09 19-02-16.png]]

- a subnet association happens.
- which adds a route to the route table for the private instance to the gateway endpoint.
- The endpoint creates a type of tunnel for the Service.
- there can be a policy forb endpoint to deny access to the buckets we want to not give access to the Subnets.


Why endpoint?
it allows to access services without letting it connect to the public network.


Important consideration:
- **Private subnets with no internet** can still access **private S3 buckets** using **VPC Gateway Endpoints**
    
- You must **configure the bucket policy to allow access from your VPC endpoint**


Bucket policy must be changed!!!!



You're referring to an **S3 bucket that has all public access blocked**, **ACLs disabled**, and **uses only bucket policies for access control** — often called an **"S3 private bucket"** under **Object Ownership = Bucket owner enforced**.

Even in this case, you can **100% use a VPC Gateway Endpoint** to **securely access your bucket** — but with **policy-based control only** (no ACLs involved).



Access to the S3 bucket will be **entirely governed by the S3 bucket policy** (not ACLs) — and you can still allow access from the **specific VPC Endpoin**


{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AccessFromVPCEOnly",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-private-bucket/*",
      "Condition": {
        "StringEquals": {
          "aws:SourceVpce": "vpce-abc123xyz456"
        }
      }
    }
  ]
}


Your **VPC endpoint** is in the same region as your bucket (must be).




This brings me to question this:
are there other ways to access a private bucket?
Yes, through IAM roles or users, and changing in bucket policy.
Also, you can access through Signed urls, but this is only for **OBJECTS**


ALSO, **Static website hosting** won’t work with private buckets (they must be public or use CloudFront)
By cloudfront you can use OAI for specific user allowance.