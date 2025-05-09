A company is launching a new internal platform for managing multiple independent projects. Each project will require its own dedicated AWS account for isolation. The company needs a solution that automates account creation, applies mandatory security guardrails, and centrally manages shared networking resources such as VPNs and subnets for the accounts. The solution must minimize manual effort and ensure compliance with security standards.

Which solution will meet these requirements with the LEAST operational overhead?

**se AWS Control Tower to automate account provisioning. Create a dedicated networking account with a centralized VPC. Use AWS Resource Access Manager (AWS RAM) to share subnets with project accounts. Enforce security guardrails by using AWS Control Tower guardrails**: This is correct because AWS Control Tower simplifies account setup with built-in security guardrails. It minimizes operational overhead by automating VPC sharing and guardrail enforcement through AWS RAM.  
**Use AWS Organizations to create project accounts manually. Deploy a VPC in a centralized networking account. Use AWS RAM to share subnets. Manually configure security policies in each account**: This is incorrect because manual account setup and security configuration increase operational overhead.  
**Use AWS Control Tower to set up accounts with pre-configured VPCs in each project account. Connect these VPCs to a central networking account through a transit gateway. Enforce security controls with AWS Config**: This is incorrect because configuring a transit gateway and enforcing controls through AWS Config introduces more complexity than required for this use case.  
**Use AWS Organizations to create accounts for each project. Deploy a shared VPC in a centralized account. Configure AWS Firewall Manager to enforce security controls. Manually configure routing for project account traffic through the shared VPC**: This is incorrect because it requires more manual effort to configure routing and lacks automation in account creation and security enforcement.


AWS Resource Access Manager (RAM) is a service that enables you to easily and securely share AWS resources with any AWS account or within your AWS Organization. It is not used for restricting access or permissions.


ram


