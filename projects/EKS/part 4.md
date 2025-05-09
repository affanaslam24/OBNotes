we need helm chart to create the alb controller
![[Pasted image 20250423142818.png]]

 The helm chart:
 ![[Pasted image 20250423143415.png]]
 Copy your vpc id of the cluster
 ![[Pasted image 20250423143516.png]]
 Q. can eks create the cluster in multiple regions? is it HA? how does it set the various nodes in different AZs, if so?


![[Pasted image 20250423143745.png]]


done



Soo now, wwe check the controller:
![[Pasted image 20250423143808.png]]
see, that its under deployment, so it is indeed a pop.
Also, it created 2 replicas.
One in each AZ.
Basically, the load balancer will be using 2 AZs for it load balancing purpose.
Itll create the ALB resources in 2 AZs.


So we found tthat the replicas were not being created for some reasons:
![[Pasted image 20250423144049.png]]


So how to debug your deployment?
Heres how:
![[Pasted image 20250423144134.png]]
![[Pasted image 20250423144144.png]]
so the status field can show the error.
OR you can use ***describe***.

the error was beause the service account wasnt created successfully.

so we are runnig this again:
![[Pasted image 20250423144328.png]]


!!!IMPORTANT
**When you are creating the service account: it uses CLOUDFORMATION.**
**SImilarly, using EKSCTL, it uses cloudformation to create stacks for your resources, so if you encounter any bugs, youu can go and delete the corresponding stacks.**

![[Pasted image 20250423144627.png]]
we deleted the old stack creating the old serviceaccount


Deleted the old helm chart that was making the load balance controller previously
![[Pasted image 20250423144727.png]]


Its possible that the pods will run but the deployment will not? nope


![[Pasted image 20250423145102.png]]


![[Pasted image 20250423145126.png]]
created the ALB automatically


**how did this get created? the ingress controller created it using the ingress resource, which provided the config for it**


Now we have the address!!

![[Pasted image 20250423145250.png]]

