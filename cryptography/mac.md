![[Pasted image 20250527134325.png]]

it provides integrity, but there is still a loop hole which needs to be addressed.

![[Pasted image 20250527134408.png]]



SO here we have the technique
![[Pasted image 20250527134543.png]]

we need a mutual key for this, which is something we will talk about later on.



So what is mac?
![[Pasted image 20250527134633.png]]

![[Pasted image 20250527134658.png]]




How to create this mutual secret key?

![[Pasted image 20250527135029.png]]

![[Pasted image 20250527135037.png]]

![[Pasted image 20250527135045.png]]

![[Pasted image 20250527135118.png]]

this covers confidentiality but to I and A

signatures in this format:

- create a hsan wiht the message, then encrypt it with the private key, attack it to the meesage, send the message and the other party can then check if its authenticated using the senders public key.
![[Pasted image 20250527135343.png]]

![[Pasted image 20250527135403.png]]

