### **NACL vs. Security Groups in AWS** 🚀

Both **Network ACLs (NACLs)** and **Security Groups (SGs)** control **traffic flow** in AWS, but they operate at different levels.

---

## **🔹 Security Groups (SG)**

✅ **What is it?**

- Acts as a **firewall for EC2 instances**
    
- Controls **inbound & outbound traffic** at the **instance level**
    

✅ **Key Features:**

- **Stateful** → If traffic is allowed **in**, the **outbound response** is automatically allowed.
    
- **Attached to EC2 instances**, not subnets.
    
- **Rules apply to all instances** associated with the security group.
    
- **Only allows traffic** (no deny rules).
    

✅ **Example Security Group Rules:**

|Rule|Type|Protocol|Port|Source|
|---|---|---|---|---|
|✅ Allow|SSH|TCP|22|My IP|
|✅ Allow|HTTP|TCP|80|0.0.0.0/0|
|✅ Allow|HTTPS|TCP|443|0.0.0.0/0|

---

## **🔹 Network ACL (NACL)**

✅ **What is it?**

- Controls **traffic at the subnet level**.
    
- Applies to **all instances** in a **subnet**.
    

✅ **Key Features:**

- **Stateless** → If traffic is allowed **in**, the **outbound response** is **not** automatically allowed.
    
- **Rules are evaluated in order** (numbered rules).
    
- Can **explicitly allow or deny** traffic.
    
- Applies to **entire subnets** instead of individual instances.
    

✅ **Example NACL Rules:**

|Rule #|Rule|Type|Protocol|Port|Source|Action|
|---|---|---|---|---|---|---|
|100|✅ Allow|SSH|TCP|22|My IP|Allow|
|200|❌ Deny|All Traffic|All|All|0.0.0.0/0|Deny|
|_LAST_|❌ Deny|All|All|All|All|Deny|

---

## **🔹 Key Differences Between NACLs & Security Groups**

|Feature|**Security Group**|**Network ACL**|
|---|---|---|
|Level|**Instance-Level**|**Subnet-Level**|
|Stateful/Stateless|**Stateful**|**Stateless**|
|Default Behavior|**Deny all inbound, allow all outbound**|**Allow all traffic**|
|Can Deny Traffic?|❌ No|✅ Yes|
|Applies To|**Instances**|**Entire Subnet**|
|Rule Evaluation|**All rules apply**|**Rules are evaluated in order**|

---

### **💡 When to Use What?**

- **Security Groups** → Control access **to instances**
    
- **NACLs** → Control traffic **to subnets**
    

✅ **Use both together** for extra security!