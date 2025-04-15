![[Screenshot from 2025-03-30 16-38-39.png]]
- can be used in different AZs.
- it ises imahes to run containers inside different AZs and instances,

2. fargate mode
![[Screenshot from 2025-03-30 16-40-01.png]]
- Fargate is ame as aurora serberless.
- it had a shared infra poil and from there an instance is selected at random insie which the containder will run.
- to acess this container =, the instance is connected to an eni in the vpc of our choice, becuse eni gives us the public or private ip.

![[Screenshot from 2025-03-30 16-41-17.png]]


![[Pasted image 20250405024756.png]]


![[Screenshot from 2025-03-30 16-46-17.png]]

And here the vpc is selected with the subnets attached for extra availibility,
Auto assign ipv4
cluster vpc
secirity group

