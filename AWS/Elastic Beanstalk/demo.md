![[Pasted image 20250412134354.png]]


![[Pasted image 20250412134406.png]]

![[Pasted image 20250412134417.png]]


![[Pasted image 20250412134432.png]]


- by now we know that an application can have various environments, inside the invironment our application versions are hosted.

- and the above method of creating Application will create an environment
![[Pasted image 20250412134628.png]]

![[Pasted image 20250412134642.png]]

![[Pasted image 20250412134703.png]]



- click the go to environment opton, because that is where your code is gonna be in:
![[Pasted image 20250412134737.png]]


In the applications section, we can see all the different environments in that applications:
![[Pasted image 20250412134820.png]]


-
different configs in the env:
![[Pasted image 20250412141037.png]]
![[Pasted image 20250412141047.png]]

![[Pasted image 20250412141054.png]]


We can also download logs, inbuolt feature: the logs is the logs form the instance inside whihc the whole configuration happened:
![[Pasted image 20250412141146.png]]
![[Pasted image 20250412141150.png]]


Events as well:
![[Pasted image 20250412141252.png]]


And see: it created resources itslef:
![[Pasted image 20250412141319.png]]
an instance
which was created using an autoscaling group, from cloudformartion:
![[Pasted image 20250412141347.png]]
![[Pasted image 20250412141410.png]]
![[Pasted image 20250412141432.png]]
created the SG as well.
As well as a VPC!


---

creating new environment:

![[Pasted image 20250412161145.png]]
![[Pasted image 20250412161155.png]]

![[Pasted image 20250412161212.png]]

![[Pasted image 20250412161228.png]]

- whats source build?
- its the archive through which we upload our source code

Configure more options:
![[Pasted image 20250412161344.png]]

![[Pasted image 20250412161353.png]]

![[Pasted image 20250412161417.png]]
1 to 4 instances


By clicking on custom config, you can set which proxy engine you want to use for your project: ngix, etc


![[Pasted image 20250412161825.png]]

![[Pasted image 20250412161837.png]]



env variables as well:
![[Pasted image 20250412161859.png]]



Then root sizes and etc:;
![[Pasted image 20250412161925.png]]



Now, you can choose on demand and combine options:

![[Screenshot from 2025-04-12 16-19-34.png]]


![[Pasted image 20250412162009.png]]


No of AZs selection:
![[Pasted image 20250412162053.png]]



And then, which Az to use:
![[Pasted image 20250412162109.png]]

Triggers for scaling
![[Pasted image 20250412162120.png]]


Load balancer:
![[Pasted image 20250412162138.png]]



![[Pasted image 20250412162200.png]]



Rules as well as access logs:

![[Pasted image 20250412162235.png]]


YOU can configure An rds database inside the beanstalk environment:
![[Pasted image 20250412162401.png]]

But beware that its INSIDE the environment. So if the environment goes wrong, then the database goes lost.
That is why try to have RDS outside the beanstalk.


- So now youve crrated a new environment, and thats hwere we will be working.
- GO to [[demo2]]