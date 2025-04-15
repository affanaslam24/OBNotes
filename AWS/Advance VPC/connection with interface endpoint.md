![[Pasted image 20250409200203.png]]

![[Pasted image 20250409203224.png]]

this will not work, because the instanc edoesnt has publoc acces


![[Screenshot from 2025-04-09 20-33-11.png]]
 ![[Pasted image 20250409203322.png]]

![[Screenshot from 2025-04-09 20-33-34.png]]

![[Screenshot from 2025-04-09 20-33-58.png]]


Now, we will see what happens if we disable this:
![[Pasted image 20250409203617.png]]

Since, intefaces uses ENIs we can configure the Security groups:
![[Pasted image 20250409203647.png]]

Full access
![[Pasted image 20250409203700.png]]

created 
![[Pasted image 20250409203715.png]]


Since we didnt enable the DNS endpoint migration or whatever, its still not allowing to send traffic
![[Pasted image 20250409203756.png]]
one way to tack;e that is:
![[Pasted image 20250409203820.png]]
using the url for endpoint
whats the endpoint adress?
![[Pasted image 20250409203900.png]]
this is



OR you can just modify private dns name
![[Pasted image 20250409204104.png]]

![[Pasted image 20250409204138.png]]
![[Pasted image 20250409204140.png]]
done


- IMPORTANT!!!- can have only one interface in each AZ. Not in Subnet, but in one AZ. IF your Az has more than one subbnet, you have to choose any specific subnet.
