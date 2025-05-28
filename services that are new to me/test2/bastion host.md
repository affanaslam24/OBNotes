private subnets dont have igw.
We know igw is required for routing network within and out of the vpc. But if a private subnet is not connectd to one, then it can be propagated inside, right?


BUT:
**Communication within the same VPC (Virtual Private Cloud) does _not_ require an Internet Gateway.**  
It happens over AWS’s **internal network**, using **private IP addresses**.

WE primarily depend on route tables for the propagation


ALso, a custom vpc does not have an igw attached to it.

and its main route table only propogates iinside the local destination.


so all the subnets are privste by defualt.
You would require a public propagation then add a route to your route tablet to an igw.