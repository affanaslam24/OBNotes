### **How to Use Roles in AWS?**

An **AWS IAM Role** is an identity that allows **temporary permissions** to AWS resources **without using username/passwords or access keys**. It is used by services, applications, and users to interact with AWS securely.

---

## **🔹 1. How Do You Use Roles?**

You use roles by **attaching them** to AWS services, users, or external entities. Here’s how:

### **✅ Use Case 1: Assigning a Role to an EC2 Instance**

To allow an EC2 instance to access AWS services **without storing credentials**, you attach an IAM role.

#### **Steps:**

1. **Create an IAM Role**:
    
    - Go to **IAM > Roles > Create Role**.
        
    - Select **AWS Service** → **EC2**.
        
    - Attach policies (e.g., `AmazonS3ReadOnlyAccess` for S3 access).
        
    - Create the role.
        
2. **Attach the Role to an EC2 Instance**:
    
    - Go to **EC2 > Select Instance**.
        
    - Click **Actions > Security > Modify IAM Role**.
        
    - Attach the IAM Role you created.
        
3. **Use the Role Inside EC2**:
    
    - Connect to EC2 via SSH.
        
    - Run AWS CLI commands: