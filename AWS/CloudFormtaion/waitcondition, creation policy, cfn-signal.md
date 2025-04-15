![[Pasted image 20250410182614.png]]

- its when we want to check if the bootstrapping done was succesful or not.


![[Pasted image 20250410182825.png]]

- for EC2 you use creationPOlicy.
- for external things or some other service or external devices, you might want to use waitCondition.
- both works the same way.


---

CreationPolicy in Ec2 or autoscaling group

![[Pasted image 20250410183137.png]]
- the opt/aws/bin/cfn-signal is used for sending the signal to the stack.
- the creationpolicy is added in the autoscaling groups
- each instacn will give one signal, and therefore there are 3 count signals.
- if a single instance fials, the whole thing fails.


----
 a waitCondition on the othher hand is not of one resource. It depends upon various resources.
 ![[Pasted image 20250410183348.png]]
![[Pasted image 20250410183519.png]]
- count understand this.


