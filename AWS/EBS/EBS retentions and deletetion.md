A company operates a self-managed Microsoft SQL Server database hosted on Amazon EC2 instances with Amazon Elastic Block Store (Amazon EBS) volumes. The company uses daily EBS snapshots for backup. Recently, an issue arose when a snapshot cleanup script unintentionally deleted all the snapshots. The solutions architect must design a solution to prevent accidental deletions while avoiding indefinite retention of EBS snapshots.

Which solution will meet these requirements with the LEAST development effort?


**Apply an EBS snapshot retention rule in Recycle Bin to retain snapshots for 7 days before permanent deletion:** This is correct because Recycle Bin provides a simple way to recover snapshots deleted by mistake. By configuring a retention rule, snapshots are stored securely for the defined duration, preventing accidental deletions without requiring custom development.

**Change the IAM policy to deny deletion of EBS snapshots to all users:** This is incorrect because it would prevent legitimate deletions of expired snapshots, which could lead to increased storage costs and operational inefficiencies.

**Implement a cross-region copy for EBS snapshots daily and set a retention policy for the snapshots in the target region:** This is incorrect because cross-region replication increases cost and complexity. It is unnecessary for this use case when the Recycle Bin can address the issue.

**Use Amazon Data Lifecycle Manager to create EBS snapshots with automated retention rules:** This is incorrect because Data Lifecycle Manager can manage retention but cannot prevent accidental deletions without Recycle Bin as a backup layer.


