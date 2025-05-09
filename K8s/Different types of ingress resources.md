![[Pasted image 20250507104316.png]]

![[Pasted image 20250507104327.png]]

- host based is when different host, that is your different domain name is used.
- Path based is where you host remains the same, domain name is same, but your routing at the end is chanigng.

***basically, in ingress reosurce, we are giving traffic rules for our load balancing purpose.***


using wldcar:
![[Pasted image 20250507104952.png]]

![[Pasted image 20250507105204.png]]

![[Pasted image 20250507105416.png]]

![[Pasted image 20250507105518.png]]

in ssl bridging, the malware is detected in the load balancing level when the packet got decrypted over there


![[Pasted image 20250507105709.png]]


![[Pasted image 20250507105829.png]]

the yaml:
![[Pasted image 20250507105845.png]]

So instead of the certificat ebeung stored in the yaml, we can store it in "Secrets" of kubernetes.

![[Pasted image 20250507110106.png]]

