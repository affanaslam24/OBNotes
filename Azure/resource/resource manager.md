![[Pasted image 20250416204106.png]]
- So every resource you create is created by resource manager.
- this resource manager is set up by Azure itslef and works to create a resource for you.
---
![[Pasted image 20250416204322.png]]
- this is how you create a resource group
- You also need to specify the subscritpion model this resource gorup will be attached to.

![[Pasted image 20250416204443.png]]
benefits of RG?
- inisde the resouce Group, you have all the groouping of the various resources you created.
- you can contorl the access of these resources in one go
- their security and various fields as well.
- Most intriguingly, whatever other resources that are created while making that resource, gets inisd ehe Group.
	- menaing, that i created a VM, and ofr the Vm it was required to have storage, key pair, etc.
	- All these resoruces gets stored in the same resource gorup, so it beocmes easy to manage
- the resources innside one RG is mappped one to one, meaning, you cant use these or see these outside of the RG you specified.


![[Pasted image 20250416204507.png]]
- IAM


![[Pasted image 20250416204536.png]]
- grouping of various resources for one project can be done easily.
- granting permisison beocmes eassy, auditing, and costing also beocmes easy based on each project.
- Tracking based on each resource group gets easy.

![[Pasted image 20250416204651.png]]
- For different environment, you can do it by havung naming conventions.
- Payment-dev, for dev
- payment-qa for qa working,etc


![[Pasted image 20250416204739.png]]
- So what weve learned is, IT grants flexibility in granting and denying access to resources as a whole.
- It creates different environment.
- Helps in billing and security per project.




![[Pasted image 20250417005453.png]]


