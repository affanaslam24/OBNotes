prereq:
- kubectl
- aws cli
- eks ctl

Now, to create the cluster, through cli:
![[Pasted image 20250421230700.png]]
- give name, region where you want it to be, and the type of cluster.


Things that this cli will configure for us:
![[Pasted image 20250421230852.png]]
- eks requires a service role, that will be created foe you

there are other configs, that we will study in depth, thst the cli creates for us:

![[Pasted image 20250421231018.png]]

, it creates the public privste subnet for us, the vpc configs and everything as well.
**Can we change these? we will see that later.**


![[Pasted image 20250421231127.png]]

created1


![[Pasted image 20250421231140.png]]

You can check your resources through the resource tabs: everything from pods health to services and ingress everything is visible:
![[Pasted image 20250421231225.png]]


What does it have?
![[Pasted image 20250421231307.png]]
- openid connection for connection with identity provider!
- certificate
- api endpoint for connection


![[Pasted image 20250423130923.png]]
openID:
- openID is what we use to connect with identity providers.
- idk the specificatins of it, but there are various identity pproviders, like google facebook and others, that casn be used for login and sign up purposes. So we can use those to connect to the users with openID endpoint.
- now, for this project, we will be using IAM as our identity providers, granting access only to the IAM users.




![[Pasted image 20250423130533.png]]
- since weve created fargate option, we wont see anything here, but incase we were using ec2 option, then we can see multiple nodes in this place as our ec2 instances.



![[Pasted image 20250423130829.png]]

- meaning, you can only deploy pods to only these 2 namespaces.


[[part-2]]