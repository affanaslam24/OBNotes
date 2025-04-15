- deployment all at once in all the instances,  and we experience a brief outage.
- in bactches we release versions, and at the same time it needs to pass the health checks
- rolling deployments means both the versions running at the same time. (IDK what this means)
![[Pasted image 20250412163712.png]]
- immutable means a new set of ASG is created and the newer verisons are deployed, but only when we want it to.
- ASG with old and new instances both, where you can determine the traffic distribution: traffic splitting.




![[Pasted image 20250412163907.png]]




![[Pasted image 20250412163928.png]]
- the batch size can be changed.
- Batches are basically number of instances htat gets changed.
- here, there is drop in capacity, because each batch while they are down means low capacity.


![[Pasted image 20250412164145.png]]
- here as you can see, a new batch is added, and this batch is basically half the original batch size.
- And when th whole process of deployment is complete, the additonal batches are removed.


![[Pasted image 20250412164314.png]]
- it has a really high cost, because double the number of instances are running at the same time for a while.
- also, only when the healthchecked passed is when the deployment happens.



![[Pasted image 20250412164800.png]]

- traffic splitting is similar just that the traffic is first split and then somethign happens.


![[Pasted image 20250412164931.png]]




