![[Pasted image 20250409222701.png]]


without transit gateway:
![[Pasted image 20250409222829.png]]

but for fully highly available:
![[Pasted image 20250409222924.png]]



Now, with transit gateway:
![[Pasted image 20250409223147.png]]
- notice that the attachments are inside the subnet of The Az where the service is required.
- Its similar to the interface endpoint where a subnet was selected in an AZ. thats where it resides, BUT other subnets can access it.
- it can transitive routing btween different services, as you can see.
- provides global network.



![[Pasted image 20250409223417.png]]


remeber these for exam.


DeMO:
[[transit practical]]


