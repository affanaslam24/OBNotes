Great question — **Launch Template vs Launch Configuration** is a common AWS interview and exam topic. Here's a clean breakdown:

---

### 🆚 **Launch Configuration vs Launch Template**
|Feature|Launch Configuration|Launch Template|
|---|---|---|
|**Current Status**|✅ _Legacy (deprecated)_|✅ _Preferred & recommended by AWS_|
|**Support for latest features**|❌ No|✅ Yes (EBS optimization, T2/T3 unlimited, etc.)|
|**Versioning**|❌ Not supported|✅ Supported (you can create multiple versions)|
|**Multiple Instance Types**|❌ No|✅ Yes (good for flexible scaling)|
|**Spot Instances Support**|❌ Limited|✅ Full support|
|**Parameter flexibility**|❌ Fixed (you must recreate)|✅ You can reuse and modify versions|
|**User Data script**|✅ Supported|✅ Supported|
|**Used with Auto Scaling**|✅ Yes|✅ Yes|

---

### 🚀 **When to Use What?**

- Use **Launch Templates**:  
    Always. AWS recommends this going forward. It supports modern EC2 features, is future-proof, and allows versioning.
    
- Avoid **Launch Configurations**:  
    AWS is **phasing them out**. Most new services and features are **not compatible** with launch configurations.
    

---

### 📘 Example Use Case:

- You want to auto scale EC2 with:
    
    - Different instance types
        
    - Support for Spot + On-Demand
        
    - Version control for changes
        

👉 **Use Launch Template with Auto Scaling Group**.

---


Per the default termination policy, the first priority is given to any allocation strategy for On-Demand vs Spot instances. As no such information has been provided for the given use-case, so this criterion can be ignored. The next priority is to consider any instance with the oldest launch template unless there is an instance that uses a launch configuration. So this rules out Instance A. Next, you need to consider any instance which has the oldest launch configuration. This implies Instance B will be selected for termination and Instance C will also be ruled out as it has the newest launch configuration. Instance D, which is closest to the next billing hour, is not selected as this criterion is last in the order of priority.

Please see this note for a deep-dive on the default termination policy:

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q65-i1.jpg)

via - [https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-termination.html](https://docs.aws.amazon.com/autoscaling/ec2/userguide/as-instance-termination.html)

Incorrect options:

**Instance A**

**Instance C**

**Instance D**

These three options contra
