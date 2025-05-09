the resrouce group
then bastion host por not
enable firewall or ot
![[Pasted image 20250416230402.png]]
the policy is what defines hwat will and will not access the instance or whatever or some shit



The CIDR block for your Vnet
![[Pasted image 20250416230501.png]]

Subnet config
![[Pasted image 20250416230525.png]]


VM creation:


Needs to be done in default subnet, you have to choose


![[Pasted image 20250416230757.png]]



![[Pasted image 20250417002438.png]]


![[Pasted image 20250417002506.png]]



firewall:
![[Pasted image 20250417002633.png]]
the firewall policy:
![[Pasted image 20250417003013.png]]

then rhe DNAt rules:
network adress translation rules
![[Pasted image 20250417003049.png]]


this is rule collection, then we have rules inside of it
![[Pasted image 20250417003123.png]]

![[Pasted image 20250417003225.png]]
look at the rule collection name

in the destination adress, write the public ip of the firwall:
![[Pasted image 20250417003354.png]]


And the translated ip adress:
![[Pasted image 20250417003534.png]]
needs tp be the ip of your vm



So, what we have here is this-
we connect to the firewall, and from the firewall we translate that to the private ip of the instance.
its like a door, then insid ethe door you can translate to the various instances using private ip and everything


done:

![[Pasted image 20250417004038.png]]



![[Pasted image 20250417010853.png]]

![[Pasted image 20250417010906.png]]

bastion:


![[Pasted image 20250417010927.png]]


