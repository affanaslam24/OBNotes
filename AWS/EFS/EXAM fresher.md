Amazon EFS is a regional service storing data within and across multiple Availability Zones (AZs) for high availability and durability.

So insid one region. INside one VPPC, at that.

SO, if you want other regions to connect to it, with real time changes, use VPC peering. Because VPC peering can be cross region as well.

For the question with spreadsheet that are shared amongst users:
. S3 does not allow in-place edit of an object. Additionally, it's also not POSIX compliant.

So one would need to develop a custom application to "simulate in-place edits" to support collabaration as per the use-case.