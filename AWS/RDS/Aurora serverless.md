its what fargate is to ecs. (gotta see what this is about.)

![[Pasted image 20250402153011.png]]

it can scale up and down based on the number of acu, o number of instances that you provision.
and its got billing based on the resources that you used.

![[Pasted image 20250402153512.png]]

Lets talk about the various things in serverless.

1. The Acu is nothing but something which makes the deployment of servers in aurora a scalabale event. It uses a pool which is managed by AWS, where it keeps a set of **warm** instances which can be shared by aws instantaneously as per the requirements of the serverless cluster. This pool is shared by various users of aws.
2. So if the cluster requires a bigger instance for its comooute operation and the old instance starts getting idle, the idle server can also be scaled down.
3. iT uses a proxy fleet which is a layer that is built right in the middle of the application and the cluster, and the traffic form the application to the alcuter is passed through this. what i mean is, since the cluster and the application are nnot talking directly, it becomes easier to scale up and down without the application being aware of the backend proceses. it creates a layer of abstraction.
4. We are never aware of these intricaries, we kust reqired to set the max and min of the acu.

![[Pasted image 20250402154455.png]]

So all these use cases are self explanatory, but the one i need to make you understand is, **The billing is incurred over what you consume, and during idle or no use of server, the database instaces can be paused as well, automatically. and during those times the billing is done only based on the storage that is consumes, which is very cost effective**


NOw,
![[Pasted image 20250402155503.png]]
This is the part where the cpacity units are configured, and the pausing effect is enabled or disabled.

Everything else is the same as configuring aurora provisoned,
