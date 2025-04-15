make a subnet group
- the database subnets. basically where the rds will stay.


make database:
	. database identifier
	. user and password
	. instance class and type
	. if its not aurora then select the size of storage.
	. vpc selection
	. subnet group selection
	. if you want the database to be accessed by things outside the vpc, then give public acess or dont. since here we doont want to expose our db, we will not.
	. create a new security group and later on change it so that it can grant acess to the application subnets.
	. you can specify which az the instance will reside to, and this part is not related to the subnet group. subnet group part is which azs to give acess to the ....ill explain later.


When creating an **RDS instance**, AWS asks for **two things** related to networking:

1️⃣ **Subnet Group** (Collection of Subnets)  
2️⃣ **Availability Zone (AZ) Selection** (Specific AZ within the Subnet Group)

---

### **1️⃣ What is an RDS Subnet Group?**

A **Subnet Group** is a **collection of subnets across multiple Availability Zones (AZs)** within a VPC.

- **Required for Amazon RDS** because RDS must operate in a VPC.
    
- AWS **automatically selects a subnet from the group** based on the chosen AZ.
    
- For **Multi-AZ RDS**, AWS uses different subnets in different AZs for primary and standby instances.
    

**Example:**  
If your VPC has subnets in **us-east-1a, us-east-1b, and us-east-1c**, your subnet group might include:

- **Subnet 1 (us-east-1a)**
    
- **Subnet 2 (us-east-1b)**
    
- **Subnet 3 (us-east-1c)**
    

---

### **2️⃣ What Does the "Choose AZ" Option Do?**

- After selecting a **Subnet Group**, AWS asks for the **specific AZ** where you want the RDS instance.
    
- If you are setting up a **Single-AZ RDS**, you must choose **one AZ**.
    
- If you enable **Multi-AZ deployment**, AWS will place a standby copy of the RDS instance in a different AZ for **automatic failover**.
    

**Example:**

- If you pick **us-east-1a**, RDS will be deployed in a subnet belonging to that AZ.
    
- If you enable **Multi-AZ**, the standby instance might be placed in **us-east-1b or us-east-1c**.
    

---

### **🔍 Key Differences**

|Feature|RDS Subnet Group|Availability Zone (AZ)|
|---|---|---|
|**What it is**|A collection of subnets in a VPC|A specific region zone (e.g., us-east-1a)|
|**Why it matters**|Ensures RDS has subnets to operate in|Determines where the primary DB instance is deployed|
|**Multi-AZ Impact**|Must include multiple AZs|AWS picks a different AZ for the standby instance|

---

### **🚀 Summary**

- **Subnet Group** = A group of subnets spanning multiple AZs.
    
- **AZ Selection** = The specific AZ where your RDS instance's **primary database** will be deployed.
    
- **Multi-AZ RDS** = Uses the **Subnet Group** to place a **standby instance** in another AZ.





make sure port 3306 is accessible in the inbound of the security group of the instances which has application 
OR
you can add the security groups of those instances to the security group attached to the db instance.