![[Pasted image 20250412130137.png]]
- so for using this, you need to have changes in your code for integration iwht it.
- it uses aws services in the background, it uses clooudformation to create your resources, and if you want, it can use elb etc.
- for every service that you might want to use, you willl have to write subsequent changes in your code. So a non technical person cant just use this service.
- mostly a deveelops or a sevelopment team uses this.



![[Pasted image 20250412131927.png]]
- multicontainer uses ecs behind the scene to spin up muliple containers


- zip or var files stored in S3, the bundle
- application is a a container over here. Not the docker container, but like a folder or a box, where the infrastructure config and everything about the required app tht we will be depoying is contained.
- Application version is the different app versions that we deploy.
- each application version has their own container or sub-application inside the Application container.
- sub container is basically an application versions config.
- Environment are classified into:
	- web server tier is designed to work with end users
	- worker tier is to proccess work in some ways from the web tiers.

![[Screenshot from 2025-04-12 13-29-57.png]]

- first, lets understand how this works:
	- we use the dns name or the cname of one of the environments.
	- we are ignorant of the backend processes that happens, we only know the dns name.
- so in background, when the load increases, or a particular service or something scales up insid the environment, based on the ASG, then along wiht that scaling, an SQS queue gets updates with a new message, for any compute related info.
- THwe Proessing ENV is where the backend processes happens. And the number of instances inside it gets scaled in and out based on  the messages in the queue. (now we dont know if each message will create a new queue or the instance scale out is bsed on the load)
-
- EB uses Blue green testing technique.
- when the testing is workable, we just switch the cname to the dns name of the testing ENV
![[Screenshot from 2025-04-12 13-30-08.png]]

and when rewuired, we can always go back to the prod env.


![[Pasted image 20250412133921.png]]
- you CAN have databases inside your Instance of EB, but then in case of changes in ENV or anything else, the Database might have chances of getting deleted, or changed.
- So it better to configure your database seperately, or use a Database service which is managed from external sources.

