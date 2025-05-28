![[Pasted image 20250527213103.png]]

what is MAC? check [[mac]], but for short:
![[Pasted image 20250527213148.png]]

message and key are both used to calculate the hash and then the reciever will check that.

**rememeber that message and key are passed through the authentication function.**


Difference between mac and hash:
![[Pasted image 20250527213412.png]]

only message no key:


---


types of authentication and their levels:

- using symmetric encryption:
![[Pasted image 20250527213541.png]]

- using asymmetrical encryption:
![[Pasted image 20250527213626.png]]


- using its own private key:
- ![[Pasted image 20250527213707.png]]


- best method:
![[Pasted image 20250527213725.png]]

this is using encryption only.

next we will learn authentication through hash and mac:

---


mac:

![[Pasted image 20250527213913.png]]

remember that we need a shared secret key on both sides for this.

![[Pasted image 20250527213957.png]]

![[Pasted image 20250527214041.png]]

![[Pasted image 20250527214102.png]]

draw this diagram in exam.


![[Pasted image 20250527214137.png]]

no confidentiality, only authentication.

for both confidentiality and authentication:

![[Pasted image 20250527214256.png]]

basically the same process, but now we are encrypting, but note that we are using different keys for encryption and different for mac generation. Check [[mac]].

![[Pasted image 20250527214505.png]]

![[Pasted image 20250527214529.png]]

