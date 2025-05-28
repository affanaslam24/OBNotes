- first we make thecluster, eks- specify the region, and fargate or ec2
- it provides api server endpoint, openid url which well use later, the service role that was created for us, the certificate
- ince weve created fargate option, we wont see anything here, but incase we were using ec2 option, then we can see multiple nodes in this place as our ec2 instances.
- we have to create fargate profiles now, to create namaspaces for our workspace of the project
- integrate the cluster with our terminal
- create a fargate profile for the namespace
- get your yaml file ready
- deployment with the label selector, image and port
- service which wikl use that selector, target port being the port that the contaier exposed, protocol to be used tcp or udb,etc
- create the ingress rresource: has host based or route based config, annotations(if things will be internet facing or internal, what kind f target type to expect), path type, revice name to expect, host name


- creation of ingress controller:
- Now, before creatino of the ingress controller, we need to configure the OIDC connector. This is a prereq, because otherwise even if we did create the LB controller insid ethe cluster, the connection will fail.

**WHys that? because we are using alb controller over here, and it needs some access permissions to talk to use the aws services, and we can give it those permissions using IAM users or roles, which we will attach trough OIDC, thats the only way to grant access to a cluster to aws resources.**


- Alright, what we need to understadn is: the ALB ingress controller that we are making is a pod in itself.
Basically, this pod will work with aws services and create a load balancer with configs for us.
And this is why we need oidc connector to connect to an iam user or role that has corresponding iam policy attached to it.


- now thart your configured the oidc, its a basic command, get the iam policy for your iam role, for the creation of alb.
- this can be down by curl, and its a standard policy
- aws iam create-policy .....
- now the created policy will need to be attached to a role, and that part can be done while we creste a service account: service account woulld need the name of your role and a policy to attach.
- why service account? pods cant do things without granting them access, oidc provider gives us AUTHORITY to make alb, it doesnt creates it, we use servbice account to give our pods that authority, grant that role for the creation of stacks and alb.
- download the helm chart
- use the helm repo to download the a;b controller, itll ask us for vpc id, service account name
- vpc id will be the vpc where the cluster is installed
Also while creating service account, it uses cloudformation stack, because its trying to download iam role and whatnot.


