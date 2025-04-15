### NACL
![[Screenshot from 2025-03-30 02-00-35.png]]
Both inbound and outbound cn rule have same numbers, it doesnt matters.

![[Screenshot from 2025-03-30 02-01-27.png]]
NACLS Are stateless, so they see it as inbound and outbound for every request and response. 
By default, all the nacls provide inbound and outbound. 
- **NACLS are provided on subnets**-IMPORTANT!!!!!

- NACLS cant provide logical adressing of AWS services like how security group does.
- It reqires physical resource adressing like Ip adresses and ports and protocols.

![[Screenshot from 2025-03-30 02-02-14.png]]

Like, you would need to know ports of both the subnets for communication. 
But with Subnet group you can connect thorugh the subnet group names itself.

DEFAULT NACL
![[Screenshot from 2025-03-30 02-02-41.png]]

Here its written **A VPC** so check later if vpc is connected with nacl or subnets.


OK, so we do have some clarity, but we need to research once more:
![[Screenshot from 2025-03-30 02-03-39.png]]

**what does it mean by connected to vpc and not subnet?**

**Also check, if i can create one nacl and connect to more than one subnet or vpc.**

HERE ARE THE ANSWERS:
![[Screenshot from 2025-03-30 02-05-20.png]]
- a nacl can be associated with many subnets
- each subnet can have only one NACl
- no logical resources
- Are configured for subnets boundary connections. IMPORTANT- **Canot effect instances inside one subnet**
- Allows explicit deny, because it is stateless, meaning it has request and responseconfig to be mmade,so it can EXPLICITLY deny or sllow traffic.
**Also, IDfference between it and SG is this, It has a portion which says 'Allow' or 'deny' in its setting. BUt SG doesnt has Anything like that.**

Here you xcan specify bad actors to specificly block  and then specify in SG  for a group of cidr range to be blocked.

### Security Group

![[Screenshot from 2025-03-30 02-06-58.png]]

- Not connected to instances, but the ENI.
- Q. can one SG be connected to more than one ENI? yes.

![[Screenshot from 2025-03-30 02-07-53.png]]

How do we use SG as infering to itself?
![[Screenshot from 2025-03-30 02-09-21.png]]
Since its refering to itself, it can connect to instance without hacing to know the ip adress.
- IMP- can be connected to different instances in different Subnet

How to use it with....
![[Screenshot from 2025-03-30 02-10-28.png]]

basically here, anything attached with SG can be seen as one unit. im not sure. **Check chatgpt**

Note: that SG doesnt has a allow or deny option, so its implicit deny to everything unless you explicitly allow anything. It doest has anything like Explicit deny.


Alright Q. if the SG epxlicitly allows a traffic but the NACl has given it as Explicit deny, will the traffic be allowed? NOPE.


### Important problem i faced:
i tried making security groups inisde terraform in a seperate module, but somehow it kept creating in a different region or something, which caused it ti be not accessed by the instacnes in the other region.
So security groups are resided where is also a good importance that needs to be looked after.



