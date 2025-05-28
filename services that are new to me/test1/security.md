|**Service**|**Primary Function**|**Use Case**|
|---|---|---|
|**IAM (Identity and Access Management)**|Manage **users**, **roles**, and **permissions**|Control who can access what in your AWS account|
|**AWS KMS (Key Management Service)**|Create/manage **encryption keys**|Encrypt data at rest and in transit using customer-managed keys|
|**AWS Shield**|**DDoS protection**|Automatically protects apps from DDoS attacks (Standard/Advanced tiers)|
|**AWS WAF (Web Application Firewall)**|Protect web apps from **common exploits**|Block SQL injection, XSS, etc. with custom rules or managed rule sets|
|**Amazon GuardDuty**|Intelligent **threat detection**|Detects anomalies, compromised accounts, or malware using ML|
|**AWS Inspector**|**Automated security assessments** for EC2, Lambda, and containers|Checks for vulnerabilities and unintended network exposure|
|**Amazon Macie**|Discover and protect **sensitive data** (e.g., PII in S3)|Uses ML to classify and protect personal or financial data|
|**AWS Secrets Manager**|Store and rotate **secrets/passwords/DB credentials**|Secure secret storage with automatic rotation and fine-grained access|
|**AWS Certificate Manager (ACM)**|Provision and manage **SSL/TLS certificates**|Easily enable HTTPS for domains and services|
|**AWS CloudTrail**|Log and monitor **API activity** across AWS|Governance, compliance, and operational/audit tracking|
|**AWS Config**|Track **configuration changes** to resources|Assess compliance with desired configurations over time|
|**AWS Organizations SCPs**|Set **Service Control Policies** across accounts|Apply guardrails for what services/actions accounts can perform|
|**VPC Security Tools**|NACLs, Security Groups, VPC flow logs|Network-level access control and traffic monitoring|
|**AWS Detective**|Investigate and analyze **security findings**|Helps you trace root causes of security issues (used with GuardDuty, etc.)|
|**Amazon Cognito**|Manage **user authentication and identity federation**|Signup/sign-in for apps, social login, token-based access|
