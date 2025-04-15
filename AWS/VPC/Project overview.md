![[Screenshot from 2025-03-30 00-09-14.png]]
So a vpc can have minimin and maxuimum ips.
here, there are 4 accounrs and 5 regions each, so a total of 40 ranges, thats what hes trying to say.

![[Screenshot from 2025-03-30 00-23-00.png]]
we have already taked about /16 divided into 16 /20 makes both of them, equal.


The cidr block of the project
![[Screenshot from 2025-03-30 01-22-44.png]]
why every 16? because /20 means 32-20=12 bits are left out.
So the 8 bits in the 12 will go to the last bit section. But the 4 bits left will be 2 to the power 4 which is 16.
So every 16 bits in 3rd block will change the subnet.