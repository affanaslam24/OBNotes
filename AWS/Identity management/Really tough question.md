```
{
    "Version":"2012-10-17",
    "Id":"EC2TerminationPolicy",
    "Statement":[
        {
            "Effect":"Deny",
            "Action":"ec2:*",
            "Resource":"*",
            "Condition":{
                "StringNotEquals":{
                    "ec2:Region":"us-west-1"
                }
            }
        },
        {
            "Effect":"Allow",
            "Action":"ec2:TerminateInstances",
            "Resource":"*",
            "Condition":{
                "IpAddress":{
                    "aws:SourceIp":"10.200.200.0/24"
                }
            }
        }
    ]
}
```

- so you have to understand that, when the region is US-West-1, the effect is ALLOW.
- meaning, if it is any other region, then the DENY all effect on EC2, will be applied.
- because stringNOTEqual.
- Try to understand: if the ***region is not equal*** to us-west-1, then deny all effect on ec2!!!
- but if region is us-west-1, then ***that particular block will not be working***
- And we will go to the lower block, and allow the TERMINATEINSTANE on the ip.


Correct option:

**Users belonging to the IAM user group can terminate an Amazon EC2 instance in the `us-west-1` region when the user's source IP is 10.200.200.200**

The given policy denies all EC2 specification actions on all resources when the region of the underlying resource is not `us-west-1`. The policy allows the terminate EC2 action on all resources when the source IP address is in the CIDR range 10.200.200.0/24, therefore it would allow the user with the source IP 10.200.200.200 to terminate the Amazon EC2 instance.

Incorrect options:

**Users belonging to the IAM user group cannot terminate an Amazon EC2 instance in the `us-west-1` region when the user's source IP is 10.200.200.200**

**Users belonging to the IAM user group can terminate an Amazon EC2 instance in the `us-west-1` region when the EC2 instance's IP address is 10.200.200.200**

**Users belonging to the IAM user group can terminate an Amazon EC2 instance belonging to any region except the `us-west-1` region when the user's source IP is 10.200.200.200**

These three options contradict the explanation provided above, so these options are incorrect.