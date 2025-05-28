A solution is required that will monitor changes to the OU hierarchy and allow stakeholders to subscribe to related alerts.


**AWS Control Tower** is a high-level service offering a straightforward way to set up and govern an AWS multi-account environment, following prescriptive best practices. AWS Control Tower _orchestrates_ the capabilities of several other AWS services, including AWS Organizations, AWS Service Catalog, and AWS IAM Identity Center, to build a _landing zone_ in less than an hour.

In this scenario, the feature mechanisms that enable the management of account drift are already built into the Control Tower. It requires no further engineering setup and avoids fragmenting administration to yet another service. This directly supports monitoring changes in the OU hierarchy, such as accounts being added or removed, enabling stakeholders to easily subscribe to alerts on these events.

Hence, the correct answer is: **Use AWS Control Tower to provision the AWS accounts. Enable account drift notifications.**

**Use AWS Control Tower to provision the AWS accounts. Set up AWS Config aggregated rules** is incorrect. Although AWS Config Rules are able to span multiple accounts, it’s primarily designed for evaluating resource configurations across accounts, not changes to an OU hierarchy.