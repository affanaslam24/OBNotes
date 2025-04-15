![[Pasted image 20250402213027.png]]
### The faults of classic load balancer:
For each time the load increases, it would have to create a new load balancer because it requires ssl certificate for each connection in the load balancer itself. and that was problem, because if 100 new increased load meant to create multiple load balancers with the ssl certificate in it and thats a hassle.
**(reaserch more on this one)**


The other is v2 where rules are used, and instead of the load balancer being increaased, its the rules that are increased and the rules can have the certificate attached to them on scaling time(not explained proeprly). the rules then distribute the load to target groups which uses the ASG for configuing the instances.


# ALB
![[Pasted image 20250402214544.png]]
Health check of ALB is more detailed, since it just doesnt checks if the website is givng a feedback or not, or if the ec2 is runnig or not, it can do specific testing based on the app behaviour and specifc details.But if any question related to performance issue or ssl certificate being unbroken,  then one should prefer Network load Balancer rather than Application load balancer.


### Rules in alb
So we have Listeners, and what it does is basically tells what to do with the required load. And for that, we need rules.
Rules tells the listener what to do with the traffic that comes to the load balancers, its conditions.
![[Pasted image 20250402230626.png]]

this is how it looks
![[Pasted image 20250402230650.png]]

So whats ALB really good at?
![[Pasted image 20250402230923.png]]

So you see, it can set up dufferent rules for different types of https request. basically, sincle its layer 7 load balancer it can look at the content and the http request to direct towards a specific target group, for which it uses rules in listeners. now this is hugely possible mostly becaus eits layer 7 and it can read layer 7 congifs.
it had rules, that is, condition which are then addressed to take specific action. in tbhe left we forward the traffic to a specific target group. in the right we redirect the traffic to a specific http request.

# NLB
doesnt uses http/s, and doesnt uses web or secure web.
Tcp, Udp, tls etc.

Cant do detail health checking,

![[Pasted image 20250403001743.png]]

thr last 2 points are something i am unclear about, so we will learn mire on that one,


**One question i need to find is -**
**Why do the alb requires encruption to break but the nlb doesnt requires to break that encrypstuion?**


![[Pasted image 20250403002207.png]]




