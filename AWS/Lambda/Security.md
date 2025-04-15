

Execcution roles are same as roles:
- they have trust policy which allows the lambda to get attached to it.
- they have a permissions policy that allows them to gain access of any services. It creates the **temporary credentials** that the lambda uses to interact with other reosurces.

IMPORTANT!!!!

It also has resource policy attached to it, which allows or denies various resources to attach to it.  Basically different aws accounts, or services like sns or s3, which might invoke it. If you deny them, they wont be allowed to access them or invoke the LAmba fjunction.

Also, important   note that- you cannot change this thorught COnsole. its allowed to let anyone access through console. you can onlt change this though CLI or API.

(reminder, till now we have only learnt about S3 having a reosurce policy, lambda having a resource policy and kms having a resource ppollicy, but kms has an integration of IAM policy as well as resource policy.)

![[Pasted image 20250407233332.png]]



### LOgging
![[Pasted image 20250407233508.png]]

If you want logging: you need to allow permission to lambda through executuoin role


Q.
Possible question: if you are trying to configure why an AWS lambda not working as expected, and you chehck the cloudwatch logs, and you dont find anything, its possiblle that you didnt configure the cloudwatch logs to be permissible by lambda.

