now, after the "kubectl apply", we have our service, deployment, ingress resource created, but we still dont havve the ingress controller to route the specific target.

how do we know? lets see it here-
![[Pasted image 20250423133557.png]]
all the piods are runnning(we had 5 replicas in deployment)


service is also runnig:
![[Pasted image 20250423133922.png]]

And notice that it has a cluster ip , meaning anyone that has access to this vpc or the cluster, can talk to this pod thorugh this cluster ip, but it doesn has an external ip. So anonymous users cant access it.



And ingress resource:
![[Pasted image 20250423134103.png]]
- this is the name
- this is the class- alb
- host hcan be anything, meaning anyone can acess the load balancer and then the service
- port is exposed
- BUT, there is no adress. itll be attached once we have an ingress controller for our CLUSTER.
- Why is this adress useful? You have to use this adress to access from the outside world

So, now we will create an ingress controller:
![[Pasted image 20250423134350.png]]
- this ingress controller needs to be attached with an ingress resource
- this controller will create a LB, but mind you, the LB in itself cant do anything of itself, again.
- it needs to know which target group to attach, which port to expose, adn all these configs are done by ingress controller when the LB is created by it.


### OIDC:
Now, before creatino of the ingress controller, we need to configure the OIDC connector. This is a prereq, because otherwise even if we did create the LB controller insid ethe cluster, the connection will fail.

**WHys that? because we are using alb controller over here, and it needs some access permissions to talk to use the aws services, and we can give it those permissions using IAM users or roles, which we will attach trough OIDC, thats the only way to grant access to a cluster to aws resources.**




![[Pasted image 20250423134938.png]]

Similar to:
![[Pasted image 20250423134957.png]]

we are just associating identity provider


---
Alright, what we need to understadn is: the ALB ingress controller that we are making is a pod in itself.
Basically, this pod will work with aws services and create a load balancer with configs for us.
And this is why we need oidc connector to connect to an iam user or role that has corresponding iam policy attached to it.

---

Creating the iam policy:
![[Pasted image 20250423140302.png]]

copy this json to the web browser and see the iam policy
![[Pasted image 20250423140337.png]]
![[Pasted image 20250423140402.png]]

![[Pasted image 20250423140407.png]]

its HUGE, but this json is provided by the ALB controller itslef, its in thier documentation, and its the standard onne, you dont need to change anything in it.
Just donwload the policy, attach it to a role and use it.


![[Pasted image 20250423140618.png]]
creation of policy

![[Pasted image 20250423140735.png]]

Attaching the policy creating to a role, and atahcing it to the service account of the pod
![[Pasted image 20250423141109.png]]

- what we are doing over here is create a service account basically.
- Why a service account? a pod in itself cant do some tasks, it needs some credentials, some configs, etc, etc. and it requires this service account to talk with the kubernetes api to perform these actions as well..
- So what we do is we create a service account with pollicies attached to it. 
- Then in the pod (in our case ALB controller pod), we attach our service account.
- THis granting us the permission to use aws resources.
- the oidc connected we associated earlier will be used for connection, well see how.


Its long enough:
go to [[part 4]]