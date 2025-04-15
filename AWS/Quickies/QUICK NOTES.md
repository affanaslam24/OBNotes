This will be the file where i add quick notes on topics. lets say i wrote something that i just realised in a moment of quick insight, so this willl be populated for that task.


vpc are region resilient?
and each refion xan hace ant ranfe  of vpc?


a quesrion, if we create a vpc, and assign it ouvlic ipv4, rhen will it conneccr ro rhe publuc network or not?
ir do i need to firt sonfigure a route table and set the internet farewat for it?

also, a vpc creaes an igw bt defauk, rufght?
no.
a custom vpc eill not have an igw.
and not havinf igw means its isolated

but a vpc has a default route tsble.
And to make sure your public subnets can acess the net, you will need to creare a new route table, then Associate the subnets to it, and remoce their associatiob to the default route table
also, add the route 0.0.0.0/0 to the table, so that it csn send any network from these subnets to outside.
and then add the aauto assign publiv ip to the respective subnets

another note, its the igw where the mappinf if rhe pricate ip to publiv ip happens. inside the vpc, everyone has only private ips


you can set your instance within a publiv subnet, and while launcuing dont allow a public ip, in this way the instance will nit have a public ip


where dpes the security group reside? sure it is connected to the eni of an instance, but where exactly does it resides?
should it lie inside the subnet? or is it insdie the vpc, ir the regiob?


a nat gateay is az resilience, and to make it refional resilience, you can have a nat in each az,
But the quesrion is, can one nat in one subnet be used for all the avaulable subnets of  a vpc? from different azs? also, if i confifure a nat will it charge? ir it chsrges only when ite usd?


an igw is refion resilient by defsult. nat gateway is not region resilient. matalb, igw ek hi kaafi hai, but you might need more than one nat gateway.


instance connect uses aws' ip adress to connect to the instance, and it depends upon if your iam identity that has acess to the instance. if your iam doesnt has acess you wont be able to connect, at the same time if in security group if you are only allowing your ip to connect it wont alloow your insrance connect to connect.


AMI have costs, and its the cost of the snapshots used to make the ami


difference between ami baking and user data

can i change the usrr data after the instance id launched?

user data needs to be base64 encoded


authentication is password and allowance isnide the servue
authorisation means if i am allowed to acess the utilities of the service or not,

There are various snapshot confugriation tpyes, like when you are restoring from aurora provisioned to serverless, you just need the snaoshot name and use restrore iption,
if you are using rds snapshot to make aurora =, then you need the arn to migrae.
And simialrly we need to configure proeprly on how different things like these will be used in provisoning the data backups and everything.



Note: we have mount targets in efs. dont get confused with target and listeners in elb. in elb we jsut put nodes on certain subnets inside the vpc which we have selected.

Note: cooldown period in load balancers scaling policies is where resources once created dont get deleted immediately because a resource once created will have incurred bill regardless. but this is different from the aurora serberless. in aurora serverless the instances provisioned will have billing as long as they are used, and will get paused once we stop using them, and in aurora provisioned an instance configured to run will have certain amount associated with it regardless. In serverless aurpra once the units stop working, only the storage will incur billing, but in Scaling policies as soon as an instance is added, the resources will chsrge money.


###### CHEAP SIMPOLE HIGH Availibily:
create an asg on scaling policy of max 1 desired 1 and min 1 instance, set the asg in 3 AZs. in this way the instance achieves avaulibility across various AZs and will not stop unless the vpc terminates.


can 2 vpc have same cidr block? or an overlapping one?

How does alb configure various traffic between multiple ips and multiple ec2 servers?
Do they have a route table?


IGw is kept where? in the vpc pr a specific subnet?

IAM roles are roles, but they can be called with different names when used with different services.
In EC, when you attach a role its called instance role wit instance profile.
in lambda, its called execution role.

WAF= web apllicatio firewa;;

the more hops, the worser quality.


for routing, hifher  prefix has higher prioriy.
same prefix ones, the one with static enabled has higher priority.
And local is always highest.


**KEY PAIRS ARE REGIONAL!!!!!!!!**

EIP cant be attached unless there is a internetgateway inside the VPC of the instance that you want it to be attached to!

when do we use triggers in lambda?


can we use docker in lambda?


