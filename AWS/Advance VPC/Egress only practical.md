
![[Pasted image 20250409204225.png]]

to test
![[Pasted image 20250409204243.png]]


Go to egress onlly
![[Screenshot from 2025-04-09 20-43-01.png]]

![[Screenshot from 2025-04-09 20-43-03.png]]

Now after selecting the required vpc, go to the route table section
![[Pasted image 20250409204420.png]]
and select the main route table

![[Pasted image 20250409204445.png]]
its the one which has prefix list form the gateway endpoint example

now, send all traffic from inside of the vpc (::/0) which is trying to gain access to the outside world. basically, every route of IPv6 will now point to the egress only route table.

![[Pasted image 20250409204639.png]]


done
![[Pasted image 20250409204714.png]]


