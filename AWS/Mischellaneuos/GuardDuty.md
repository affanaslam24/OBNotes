![[Pasted image 20250410130752.png]]
- protects unusual activities inside accounts


![[Pasted image 20250410130844.png]]


what does guard duty exactly do?
**Amazon GuardDuty** is a **threat detection service** that continuously monitors your AWS accounts and workloads for **malicious activity and unauthorized behavior**.


**GuardDuty** is like a **security guard for your AWS environment.**  
It watches for suspicious actions, alerts you if something shady happens, and helps you secure your infrastructure.


### **Examples of Threats GuardDuty Detects:**

- EC2 instance communicating with a **Bitcoin mining pool**
- Unusual **API calls** from a region you don’t use
- S3 buckets being **accessed anonymously** or **exfiltrated**
- Use of **stolen credentials**
- Attempt to escalate IAM privileges


So basically it watches over hwat we are doing with our services, and if those services are not doing anything out of ordinary than for what we configured it for, on the basis of maliciousness and threat.


Let’s say a developer's credentials were stolen and used from a country your org doesn't operate in. GuardDuty might trigger an alert like:

> "**UnauthorizedAccess:EC2/SSHBruteForce** – An external IP is trying to brute-force SSH into your EC2 instance."

You can then automate a response via Lambda or manually investigate it.


|   |   |
|---|---|
|**GuardDuty**|Detects threats (intrusion detection system)|

|   |   |
|---|---|
|**AWS WAF**|Blocks malicious web traffic|

|   |   |
|---|---|
|**Security Groups/NACLs**|Control who can talk to what|

|   |   |
|---|---|
|**AWS Config / IAM Access Analyzer**|Monitor and analyze your security posture|




Amazon GuardDuty is a threat detection service that continuously monitors for malicious activity and unauthorized behavior to protect your AWS accounts, workloads, and data stored in Amazon S3. With the cloud, the collection and aggregation of account and network activities is simplified, but it can be time-consuming for security teams to continuously analyze event log data for potential threats. With GuardDuty, you now have an intelligent and cost-effective option for continuous threat detection in AWS. The service uses machine learning, anomaly detection, and integrated threat intelligence to identify and prioritize potential threats.

Amazon GuardDuty analyzes tens of billions of events across multiple AWS data sources, such as AWS CloudTrail events, Amazon VPC Flow Logs, and DNS logs.

With a few clicks in the AWS Management Console, GuardDuty can be enabled with no software or hardware to deploy or maintain. By integrating with Amazon EventBridge Events, GuardDuty alerts are actionable, easy to aggregate across multiple accounts, and straightforward to push into existing event management and workflow systems.



![[Pasted image 20250413193828.png]]




Amazon GuardDuty offers threat detection that enables you to continuously monitor and protect your AWS accounts, workloads, and data stored in Amazon S3. GuardDuty analyzes continuous streams of meta-data generated from your account and network activity found in AWS CloudTrail Events, Amazon VPC Flow Logs, and DNS Logs. It also uses integrated threat intelligence such as known malicious IP addresses, anomaly detection, and machine learning to identify threats more accurately.

**Disable the service in the general settings**

Disabling the service will delete all remaining data, including your findings and configurations before relinquishing the service permissions and resetting the service.


**Suspend the service in the general settings** - You can stop Amazon GuardDuty from analyzing your data sources at any time by choosing to suspend the service in the general settings. This will immediately stop the service from analyzing data, but does not delete your existing findings or configurations.




## ✅ **What GuardDuty _CAN_ do** (including for EC2):

GuardDuty is a **threat detection** service — it uses machine learning, anomaly detection, and threat intelligence to monitor your AWS accounts and workloads for **malicious or unauthorized activity**, especially:

### 🕵️‍♂️ For EC2 Instances:

- Detects **suspicious behavior** like:
    
    - EC2 connecting to a known **malicious IP/domain**
        
    - Unusual port scanning
        
    - Brute-force SSH attempts
        
    - Crypto-mining activity
        
- Flags **unexpected communication** with known **command and control (C2)** servers
    
- Watches for **API calls** from compromised instances
    
- Monitors **network traffic** using **VPC flow logs** and **DNS logs**
    

---

## ❌ **What GuardDuty _CANNOT_ do**:

- It does **not** perform **vulnerability scanning** (e.g., checking for outdated packages, open ports).
    
- It does **not** block attacks (it's _detection_, not _prevention_).
    
- It does **not** show detailed config issues like security misconfigurations in EC2 AMIs.
    

---

## 🔐 If You Want to Check for Vulnerabilities:

Use **Amazon Inspector** (not GuardDuty):

### 🔍 Amazon Inspector:

- Scans EC2 instances and container images for:
    
    - **Software vulnerabilities** (CVEs)
        
    - **Exposed ports**
        
    - **Security misconfigurations**
        

You can use **GuardDuty + Inspector together** for full coverage:

- GuardDuty: Real-time **behavior-based** threat detection
    
- Inspector: **Static vulnerability** scanning
    

---

## 🧠 TL;DR:

|Tool|Detects Runtime Threats|Finds Vulnerabilities|Blocks Issues|
|---|---|---|---|
|GuardDuty|✅ Yes|❌ No|❌ No|
|Inspector|❌ No|✅ Yes|❌ No|
|Security Groups / WAF|❌ No|❌ No|✅ Yes (Blocks)|