
![[Pasted image 20250413194814.png]]

## Kaunch config and temopale

![[Pasted image 20250403002311.png]]

![[Pasted image 20250403002353.png]]



![[Pasted image 20250403002528.png]]
We can adjust the desured, mac and min size manually or using a scaling policy


![[Pasted image 20250403002706.png]]


Autoscaling group will launch the instances on the subnets its configured to launch into, and it needs to be attached inside a vpc. And it tries to keep things even,, meaning that if there are 3 instances that needs to be run and there are 3 subnets hat are configured, then each subnet will have one instance inside of it.
![[Pasted image 20250403003151.png]]


**Q. can an autoscling group be attached to multiple vpc?**


## Scaling policies.
![[Pasted image 20250403004302.png]]

simple is based on the metric, cpu usage, memory etc and can sometimes be used with cloudwatch agents, and sometimes can be used without ec2 services as well, like the size or the messages in sqs queues.

in stepped scaling, its more like a derailed config on how to scal up or down based on metrics.

## Self healing
Instances would be placed by ASG if it gets terminated or error or stops. Keyword, ASG would simply  REPLACE it. Any prooblem, and it will replace the instance.


###### CHEAP SIMPOLE HIGH Availibily:
create an asg on scaling policy of max 1 desired 1 and min 1 instance, set the asg in 3 AZs. in this way the instance achieves avaulibility across various AZs and will not stop unless the vpc terminates.



![[Pasted image 20250403005418.png]]

![[Pasted image 20250403005605.png]]

![[Pasted image 20250403005716.png]]


![[Pasted image 20250403005932.png]]
Tjis pme is important.


![[Pasted image 20250403010025.png]]
Very inflexible.

![[Pasted image 20250403010149.png]]
look at the 4th and 5th one, since min is set to 1, it wont got less than that 
