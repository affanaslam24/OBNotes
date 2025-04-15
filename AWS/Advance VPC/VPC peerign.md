![[Pasted image 20250409205031.png]]
- important is: 2 vpc need one vpc peering
- **since SG reside inside a REGION**, it can be used to reference the 2 vpcs.
- cant be transitive, foer that you will need 3 Vpc peerings.
- Needs routing config. At the same time, the SG and nacl will filter as well.

![[Pasted image 20250409205401.png]]
- both side you need to refer to the ranges of ip that would transfer and recieve through the **vpc peering endpoint**
- Make sure the cidr raNGES dont overlap.
- cant be transitive, unless you are using transitive gatewayu
- can be sent thriugh global network for ceoss region

---
 demo
 - we will be creating 3 vpc and all of them will have **Private Isntances**.
 - we will use sessions manager for connection.

![[Pasted image 20250409205845.png]]
cant ping to the private instNCE of another vpc


All of thm are private vpcs.


now, go to the peering connections option
![[Pasted image 20250409205934.png]]

![[Screenshot from 2025-04-09 21-00-02.png]]
requester.
![[Screenshot from 2025-04-09 21-00-12.png]]
requested/acceptor

Am=nd then you will have to accept the connection:l
![[Pasted image 20250409210136.png]]
![[Pasted image 20250409210145.png]]

Now, we have to configure routing:

this needs to happen on both sides.
![[Pasted image 20250409210246.png]]
![[Pasted image 20250409210305.png]]
for route table of vpc a

![[Pasted image 20250409210333.png]]
for vpc B


Still no comnection:
![[Pasted image 20250409210357.png]]

because of security filters!!!!
![[Pasted image 20250409210432.png]]
the security group of instance A
that was the outbound of vpc A, because we are sending traffic from inside of instance t outside of it.

in instance B
![[Pasted image 20250409210532.png]]
we check the inbound, becaus ewe are recieving traffic. And here we can see that the ports are not allowing the vpc from vpc A

**Heres the trick!!**:
Since they are fron the same region, we can add the security group logical resource id to the security group of instsnce B
![[Pasted image 20250409210726.png]]

![[Pasted image 20250409210751.png]]

Added.


working'
![[Pasted image 20250409210810.png]]


	But vpc B cant send outbound to Vpc A, because its still not configured in security group.




![[Pasted image 20250409210936.png]]

if two networks are not connected, or peered, their security groups cant be put in the security group page, inbound one.







