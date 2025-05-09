![[Pasted image 20250507100545.png]]
these are the facilities that ingress came and solved

problems without ingress:
![[Pasted image 20250507100912.png]]
- it wasnt providing solution to enterprise level or tls load balancing, meaning:
	- it wastn providing sticky sessions
	- no tls security
	- no path based routing
	- no host based routing
	- no ratio based routing
- to have those facilities installed, we would require to use cloud providers which were costing us money.
- At the same time, for lload balancing purpose using clouud provider, if there were load balancing on upto 1000 services, then there were basically 1000 static ip adresses configured, and cloud providers were charging huge miney on it.
- the problem was, for each service, there was a load balancing confiured. In the old traditional way, there was only one load balancer which was routing between various services. we are talking about microservices.
 ![[Pasted image 20250507101248.png]]

---

how does ingress works?
you create ingress resources, and the ingress controllers looks out for these resources and works based on the config written isnide the ingress resource.

ingress controller is downloaded using helm charts or yaml manifest.
![[Pasted image 20250507101914.png]]



---


A logical understanding is:

![[Pasted image 20250507102032.png]]
- lets say you wanted to deploy a pod, you write the yaml file for it, and the KUBELET deploys it.
- similarly, you write a service yaml file, and KUBE PROXY is the one that makes an ip-table for routing.
- So there is an intermediatory which looks at the requirements and makes the required changed to your cluster:
	- so we have ingress resources which have the necessary requirement, and ingress controller that makes these requirements come true.


FUnctionalities that oyu need to remember right off the bat:
- provides config for load balancing and routing like:
	- host based routing
	- path based routing

examlpe with host based routing:
![[Pasted image 20250507102650.png]]
so at foo.bar.com/bar, we will be routed to our service named 'service1', and this service can have multiple pods.

***and in here, we can write more path type and more  path that the ingress can take you to, like /login, /page, /people, etc in one load balancing itself.***
***And previously you would have to create load balancing for each of these routes using service, but now all the services can be routed in one ingress.***


---
 ingress controller:
![[Pasted image 20250507103146.png]]
it creates the nginx loadbalancer based on the nginx config that we write inside our ingress controller.


![[Pasted image 20250507103955.png]]

2nd question:

![[Pasted image 20250507104033.png]]

![[Pasted image 20250507104123.png]]


---


[[Different types of ingress resources]]
