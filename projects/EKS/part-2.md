![[Pasted image 20250423131035.png]]
- now instead of going over to console to check the clster, we can do it through our terminal

after configuring eksctl with the required cluster, we can nowmake changes to the cluster from terminal

here:
![[Pasted image 20250423131408.png]]
we are creating a fargate profile, they contain the namespace, and we need to basically have a new namespace for our application or where the pod will run

SEE:
![[Pasted image 20250423131607.png]]



The yaml file for our pod:
![[Pasted image 20250423131658.png]]

it is in this link:
![[Pasted image 20250423133324.png]]



So basicslly
![[Pasted image 20250423131749.png]]
the fargate profile that we created has a namespace configured to the cluster, but the pod will be the one to create it. this .yaml will create it, in the first line.



the deployment parT:
![[Pasted image 20250423131858.png]]



the service:
![[Pasted image 20250423131946.png]]
its using nodeport

Two things to be mondful of while having services and deployment:
- port mapping
- label and selectors
1. Notice how the deployment container port is open to port 80, and in the service- the target port and port to be exposed is 80.
2. next, in the service we have selector as app.kubernetes.io/name: app-2024, what thid does is, checks for a deployment with similar selector configuration/label, and then connect to it. This is how a service is mapped along with a depployment.
3. the selector option in deployment matches itself with the required matchingLabel, also note that the label in deployment is also same.
![[Pasted image 20250423132817.png]]
services selector should match with THIS.


Using this, the service will be able to discover the pods.



INGRESS:
- Routing the traffic inside the cluster.

![[Pasted image 20250423132955.png]]

- what are annotations: its specifications for the ingress load balancer. target type is ip adress mapping, scheme is internet facing, etc ,etc


We are using alb:
![[Pasted image 20250423133128.png]]

And whenever it matches the following rule: it will match it to the service called service-2048(our service name)
![[Pasted image 20250423133150.png]]


  

[[part 3]]