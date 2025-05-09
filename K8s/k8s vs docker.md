![[Pasted image 20250426174116.png]]

- single host
- is ephemeral
- has short life span, can die easily 
- and reviving it can be a manual task

![[Pasted image 20250426174240.png]]
- there could be 100 or 1000s of containers, adn it could get tedious to do docker ps to check which containers are running and which are not, to restrart them.

![[Pasted image 20250426174513.png]]

- you will have to auto scale manually.

![[Pasted image 20250426174629.png]]
- so docker doesnt supports any of these directly.

--- 
how does k8s help?
- single host
- auto scaling
- auto healing
- enterprise level support.

---

- usig k8s we get a cluster with multiple nodes, inside which we can send our pods, and if any certain pod has issues, we can migrate it to another node inside the cluster.
- to tackle the auto scaling issue, we have something like **replica sets**
- whenever the api server finds out if the container is oging down, it spins up a new container, thats how it tackles auto healing 