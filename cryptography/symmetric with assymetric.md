![[Pasted image 20250525142458.png]]


![[Pasted image 20250525142616.png]]

pam will encrypt the key and send it to jim
jim will use his own private key to decrypt it


now they have both identical secret key for symmetric encryption
![[Pasted image 20250525142711.png]]

![[Pasted image 20250525142726.png]]

![[Pasted image 20250525142746.png]]


this concept is:
![[Pasted image 20250525142815.png]]



using signatures: you gain, integrity and authentication of the send message
![[Pasted image 20250525142402.png]]



so this hybrid method has its limitation, it cant just prove signature test 
![[Pasted image 20250525143010.png]]

to tackle that we can use hashing algo in a small sample inside the message



---

process of using hashing with asymmetric

![[Pasted image 20250525143121.png]]

first we generate the hash from the message

that digest is then encrypted using the private key:
![[Pasted image 20250525143155.png]]

![[Pasted image 20250525143206.png]]


now jim can use the public key of pam to verify the signature:
![[Pasted image 20250525143237.png]]

![[Pasted image 20250525143248.png]]

now to verify if the integrity remains the same: he can use the same hashing algo to check if the digest has the same value

if the digest of both are same, this proves that signature is verified.



![[Pasted image 20250525143501.png]]
so using the hashing algo, we verified the integrity
and using the fact that only pams public key could decrypt the hash, it proves authenticartion




![[Pasted image 20250525143511.png]]



![[Pasted image 20250525143558.png]]

	