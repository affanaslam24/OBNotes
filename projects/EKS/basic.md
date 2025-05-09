![[Pasted image 20250421222416.png]]
- so what we see over here is, lets say we have a cluster with 3 master nodes, and 2 worker nodes, and lets say they are your ec2 servers.
- there would be 3 ways the connectivity or networking of the pods inside the worker node can be managed:
	- cluster ip= with cluster ip associated to the pods, they can communicate withing the cluster only. Nobody outside will be able to connect or request to them. a user wont be ablle to call to them.
	- NodePort: 
		- with nodeport the pods are now connected to the ip adress of the nodes. this requires configuration, but the overview is- that your pods can be accessed through the ip address of the node that you allow it to attach with.(you mention which node to attach the networking abilities with, you can configure it with the worker node where its residing or with the master node, etc). 
		- curcial thing to understand about node port is, even though the pods can now be accesed from outside the cluster using the ip adresses, there is still limitation. 1. the cluster can be made inside a **private subnet**, so only people who have access to the privste subnet can access it. 2. services, like other ec2 instaces inside the vpc can access it, but services outside the vpc might not be able to access it. 3.The ip adresses can change as well, although You can attach it with an elastic ip 
	- LoadBalancer: With this you can attach your nodes with elastic ip or public ip, and then attach that ip with a load balancer for public access. Limitations:
		- you will have to give public ip or attach elastic ip to the required number of pods or nodes inside wich they are residing, and the number of allocation o these ip addresses or the atttachechment can go upto 10,000 or more, i you have that many pods running, and this is not cost effective.
		- You will have to give public access to your nodes, and it can be security vi=ulnerable.
And this is where ingress comes into picture.

Also, you would need to encapsulate your pods with a Service layer inside the cluster for them to work with these networking terminology.


- Ingress still uses services for a pod, and the service can allow nodeport or clusterIp.
- both of them will have different configs and functionslities, but just know that ingress can suppoer both.

- ingress will basically route the traffic inside the ***cluster***.
- SO what we do is encapsulate the **service** with an ingress resource.
- We write an ingress.yaml file, and inside the yaml file we write:
	- an api call that will be sent through the user (example.com/absapi)
	- and then the yaml file says, whenever this is hit, forward traffic to the ***service***, and that should forward it to the ***pod***.
- we deploy this using kubectl inside the node of the cluster.

Now, just by writing the ingress.yaml and then having an ingress resrouce with your pod will not allow users to access the application in that pod.
**For that you need ingress controller, or basically someone that takes the user request from public internet to the ingress resrouce**

Ingress controlles:
- so you create an ingress controller based on the load balancer you are using, it could be nginx, fy, or aws elb as well.
- most of the famous load balancers have a ingress controller config with them
- So what you do is create an ingress controller inside your **cluster**, which is responsible for routing of the traffics in and out of the node, THROUGH rhis load balancer.
- IT can optionally create the AWS elb for you in the public subnet of your cluster or whatever and connect your nodes with it adn whatnot.
- Basically creating an LB environment for your traffics or for your ingress resource.


![[Pasted image 20250421225005.png]]

Lets take for example: Nginx load balancer

- an nginx ingress controller will be created inside your cluster, And this will either create an nginx load balancer for you, or you can have an existing pod with the load balancer created with the required nginx config masde for you.
- next, the nginx controller will be configured to lsiten to the ingress resource associated with it.
So lets say you have a cluster with fy ingress controller, nginx ingress controller, and aws elb ingress controller, how will they each maintain traffic?
- they will each be configired to work with particular inngress resources, and the ingress resources will also in return be mad ein such a manne rto connec to them.

So when a user tries to connect- a load balancer is connecte diwth the ingress controller, the controller then finds the subsequent ingress resource and figures which service to forward the traffic to- the traffic is sent to the service, then to the pod.



 