rds
-- we will need to create subnet groups
-- subnet group will be the subnets where we wiull store out rds
-- here it will be sn-db-A, B, C.
-- RDS is availibility zone based
-- so here we are putting the three instances in A,B,C

-- make sure the security group is connected, 3306 needs to be exposed
-- itll have db name identifier password and all that
-- we willl need to make use of rds endpoint and port

for subnet group
-- need vpc, name, the azs, the subnets

for databse
-- select the server
-- templetes = free tier
-- deployment option is single tier
-- identifier name - a4lwordpress
-- set master name - same as above
-- set the password- same as above
-- (we need to make sure the password and name is same as the configuration we are gpin too do)
-- instance class type - whatever is in  free tier - db.t4g.micro
-- storage type- general purpose ssd
-- 20gb storage
-- select vpc, subnet group, create a new security group that will allow mysql type connection
with port 3306 expposed to specific places
-- we can also connect to ec2 instances but here we will not use that option

-- no preference on the az where the instance will stay
-- no public access



efs
-- so we would create mount targets at specific subnets. and here we would be hsing
-- subnet for sn-appA B C. At the same time we would need a security group that wouuld
-- allow connection between eachb of them. (learn more about security groups, are they vpc based or subnet based?)
-- the next procedure is to configure the efs from inside the ec2 server.
-- for efs port 2049 needs to be open, and connectivity of security group is cruscial

vpc
subnet
security group whichallows 80, 22, and itslef?


use that efs in ec2
user data 
