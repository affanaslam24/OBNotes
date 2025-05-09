### ✅ **Can snapshots be shared across AWS accounts?**

Yes — **Amazon EBS snapshots**, **RDS snapshots**, and **Aurora snapshots** can be **shared with other AWS accounts**.

#### 🔹 For **unencrypted snapshots**:

- You can directly share them with specific AWS account IDs or make them public (not recommended for sensitive data).
    
- Works easily because there's no encryption key dependency.
    

#### 🔐 For **encrypted snapshots**:

- You **can share them**, **but** you must also **share the AWS KMS key** used for encryption with the target account.
    
- The receiving account must have permissions to **use the KMS key** to access and restore the snapshot.
    

---

### ✅ **Can AWS KMS keys be used in cross-account scenarios?**

Yes — **AWS KMS keys** can be used **across accounts**, but you must configure **key policies** and **grants** properly.

#### 🔸 To share a KMS key:

1. Edit the **KMS key policy** to allow another account (or its IAM roles) to use the key.
    
2. Optionally, create a **grant** to give specific permissions like `Encrypt`, `Decrypt`, or `ReEncrypt`.
    

#### 🧠 Example use cases:

- Decrypting shared snapshots
    
- Encrypting new resources in a different account using a shared key
    
- Allowing cross-account Lambda or EC2 access to encrypted S3 data