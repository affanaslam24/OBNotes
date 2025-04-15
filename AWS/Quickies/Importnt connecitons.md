- In S3, you cannot have logging of it wihtout expliicitly setting it up with cloudtrail or S3 logging feature or something.
- S3 doesnt have DDos protection.
- It doesnt have security from WAF or any other security group.
- I am not talking about the who can access it. I am saying, even the 4xx requests. Even if your bucket is private, somebody trying to access it will get an access denied message with a 4xx error code, and thats still a request for whih you will be charged.
- Even if you set a proper Cloudfront with a good OAI, there is an acess denied message that you might still get.
- Check about this proeprly later on.
---

- a very interesting take on lamda
- so each task that you specify, or each process that you set up for kambda, it will create a server for you.
- now, for each process, you are having to create a lambda, basically. 
- which does sound workable and ok, but most programing languagw can make applications such that they can handle multiple requests, multiple processes at one.
- NodeJs, with async option can handle concurrent users at once.
- python by default only handles one request, burt with django and celery can handle concurrent requests as well.
- so to say, one lambda server, which is a server eventually should be able to handle more than one request. basically, one instance has enough resources to work on multiplen pricesses.
- BUT lambda doesnt provides that.
- it talks about instant scale up and down, which is beneficial, but we are forgetting the performance tradeoff.
- Also, in concurrent, one account can have only an N number of lambda servers.

ALso, we need to study about this, but as it seems a fargate is much better serverless, but the tradeoff is, fargate cant scale down to 0, whereas a lambda can.
in fargate the processes can compte in concurrency? need to check

---

