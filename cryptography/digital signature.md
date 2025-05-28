for suthentication and integrity
![[Pasted image 20250525142402.png]]

check out how assymetric keys are used for signature: 
- we use hash of the message, then encrypt it using the private key of the sender, then send it to the reciever who can then decrypt it using the public key of the reciever and then check with the hash.
Check out [[mac]], to understand the whole proccess of MAC, as well as this mutual key exchange.
Remember that MAC is used over single symmetric key exhcange. And it also provides integrity and authentication just like when you apply the assymetric signature exchange

---


Now lets talk about Digital Signature Algo

![[Pasted image 20250527140949.png]]

![[Pasted image 20250527141003.png]]



![[Pasted image 20250527142425.png]]

![[Pasted image 20250527142516.png]]



---


theory for digital signature

![[Pasted image 20250527214642.png]]

![[Pasted image 20250527214711.png]]

![[Pasted image 20250527214809.png]]

things to note: 
- signature generation
- verification
- message and signature is sent together

signature using hash value:
![[Pasted image 20250527214935.png]]
we studied this in the practical network videos as well, that hash can be used for integrity and authenticaiton like this.

signatures in this format:

- create a hsan wiht the message, then encrypt it with the private key, attack it to the meesage, send the message and the other party can then check if its authenticated using the senders public key.
![[Pasted image 20250527135343.png]]

![[Pasted image 20250527135403.png]]

![[Pasted image 20250527215231.png]]

![[Pasted image 20250527215306.png]]

![[Pasted image 20250527215343.png]]

---

usually it doesnt provides confidentiality but to add that to the mix:
![[Pasted image 20250527215458.png]]

