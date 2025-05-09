![[Pasted image 20250409220800.png]]

- private vifs give you access to vpcs and aws private zone.
- Public  vifs give you connectivity to public zone services, likes sns sqs s3 etc.
- A port is connected to your customer router, oor a partner router. its your job to make sure the port is connectable to your router.
- one dx can have multiple vifs.


![[Pasted image 20250409221228.png]]
- so you have a customer router or a partner router inside of Aws Dx location which connects to the port given by the Aws, and t his is a physical connection. This connection gets extended to your on prem router.
- it is physical so no HA or encryption, but you can encrypt your data from the on prem ooitslef.
- each VIF should have a V:AN or BGP session for itslef. One VIF=one VPC, and thusm you canhave multiple VIFS.



![[Pasted image 20250409221612.png]]


- You manage the encryption

A workaorund this is:
![[Pasted image 20250409221818.png]]
- note that we srill use Virtual PRivate gateway for coneection between vpc and on premesis.
- THIS IS A VPN CONNECTION
- And this vgw uses endpoints in public zone of aws, and we can make use of that endpoint for the connection in encryted format by making use of IPSEC!




Arch:
![[Pasted image 20250409222148.png]]

problems:
![[Pasted image 20250409222214.png]]


Fixes:
![[Pasted image 20250409222336.png]]

![[Pasted image 20250409222443.png]]


![[Pasted image 20250409222534.png]]


DIRECT connect VS SITE TO SITE VPN





The most resilient solution is to configure DX connections at multiple DX locations. This ensures that any issues impacting a single DX location do not affect availability of the network connectivity to AWS.

Take note of the following AWS recommendations for resiliency:

_AWS recommends connecting from multiple data centers for physical location redundancy. When designing remote connections, consider using redundant hardware and telecommunications providers. Additionally, it is a best practice to use dynamically routed, active/active connections for automatic load balancing and failover across redundant network connections. Provision sufficient network capacity to ensure that the failure of one network connection does not overwhelm and degrade redundant connections._