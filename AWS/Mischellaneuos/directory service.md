- Stores assets adn identity
- ![[Pasted image 20250410104547.png]]
![[Pasted image 20250410104733.png]]


- opensource, samba, samba 4 = active directory
- ![[Pasted image 20250410104949.png]]

- thrre are users withiiin the AD that you cn sign in to.
![[Pasted image 20250410105132.png]]
- so we are basically using the identity inside the AD to connect to the on prem directory using a direct connet or VPN option.


![[Pasted image 20250410105323.png]]

- it has no functionality, it just acts as a proxy.
- and it can fail if the private directory fails.

![[Pasted image 20250410105440.png]]



A global retail company needs to provide its remote IT operations team with secure access to AWS resources across multiple AWS accounts. The company uses an on-premises Microsoft Active Directory for centralized user authentication and authorization. The AWS accounts are managed through AWS Organizations and support various internal teams and projects.

The company wants to integrate its existing Active Directory with AWS to centralize identity management, reduce operational overhead, and ensure secure, role-based access to resources across all accounts.

Which solution will meet these requirements with the LEAST operational overhead?

**Use AWS Identity Center (AWS IAM Identity Center) integrated with AD Connector to link the on-premises Active Directory. Configure permission sets in IAM Identity Center to assign account-level and resource-level permissions based on Active Directory groups:** This is correct because AD Connector allows seamless integration with the on-premises Active Directory without duplicating or synchronizing identities. When combined with IAM Identity Center, permissions can be centrally managed using permission sets mapped to AD groups, minimizing operational effort and ensuring consistent access control across multiple AWS accounts.

**Deploy AWS Managed Microsoft Active Directory using AWS Directory Service. Establish a one-way trust relationship with the on-premises Active Directory. Use IAM roles mapped to Active Directory groups to provide resource access in each AWS account:** This is incorrect because setting up AWS Managed Microsoft AD introduces additional overhead compared to using AD Connector. It requires managing a separate AWS-hosted directory and maintaining trust relationships with the on-premises directory.

**Create individual IAM users for each team member. Assign permissions manually to each IAM user in every AWS account. Use AWS Config to enforce compliance with access policies across accounts:** This is incorrect because creating and managing individual IAM users for a globally distributed team across multiple AWS accounts is operationally intensive and prone to errors. Additionally, AWS Config does not reduce the complexity of manually assigning permissions.

**Deploy an OpenID Connect (OIDC)-compatible identity provider and integrate it with the on-premises Active Directory. Use the identity provider to generate tokens for users and configure IAM roles to allow access to AWS resources:** This is incorrect because setting up an OIDC-compatible identity provider adds unnecessary complexity for a workforce identity management use case. It is more suited for customer-facing applications than for internal employee access to AWS resources.

