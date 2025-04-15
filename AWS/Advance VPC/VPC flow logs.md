- has metadata, no content.
- meaning, source and destination ip, and packet details, but not the other things insid eht epacket.
- can be used to log that data in S3, which can be accessed directly and then used by 3rd party software for comparison and wa=hatnot.
- can be used with cloudwatch llogs, which canbe further used with aws servcies and other metric related functionalities.
- ![[Pasted image 20250409180923.png]]
- did not understand the athena, but know that it uses adhoc for queries, and is billed for whateve ris being queried or some shit.

THis is how it looks architecturally:
![[Pasted image 20250409181119.png]]
it records as flowlog records.
Any log configured with a subnet will have all its eni's logs collected.


Alright:
![[Pasted image 20250409181642.png]]
this is how the flow log record looks like
- not ethe protocol numbering for icmp, tcp, udp.
- Also, now we are gonna talk about Stateless and steteful records in them:
	- if there is only one record, which shows oonly accept, then that is for the stateful firewall, meaning for security groups firewall config.
	- if there is 2 record like the one in th epic, then that means there are stateless firewall configured, meaning a NACL on the subnet.
	- Similarly, there must be a way to understand if both of them are restricting.
	- so always note the accept, reject tags for similar records
- note that metadata of the intance 169.254.169.254 doesnt shows any flow log records.


### Use Hints Based on Behavior

|Behavior|Likely Caused By|
|---|---|
|Return traffic being denied (e.g., response to an accepted inbound connection)|**NACL** (since SGs are stateful)|
|Specific IP blocked in one direction only|Could be **NACL** (inbound/outbound separately)|
|All traffic allowed except a specific port or protocol|Could be **Security Group** if it’s per protocol/port|


