
A company has a serverless application made up of AWS Amplify, Amazon API Gateway and a Lambda function. The application is connected to an Amazon RDS MySQL database instance inside a private subnet. A Lambda Function URL is also implemented as the dedicated HTTPS endpoint for the function, which has the following value:

`https://12june1898pil1pinas.lambda-url.us-west-2.on.aws/`

There are times during peak loads when the database throws a “too many connections” error preventing the users from accessing the application.

Which solution could the company take to resolve the issue?



---

too many connections is different from throttle


If a "Too Many Connections" error happens to a client connecting to a MySQL database, it means all available connections are in use by other clients. Opening a connection consumes resources on the database server. Since Lambda functions can scale to tens of thousands of concurrent connections, your database needs more resources to open and maintain connections instead of executing queries. The maximum number of connections a database can support is largely determined by the amount of memory allocated to it. Upgrading to a database instance with higher memory is a straightforward way of solving the problem. Another approach would be to maintain a connection pool that clients can reuse. This is where RDS Proxy comes in.

![](https://media.tutorialsdojo.com/amazon-rds-proxy.jpg)

RDS Proxy helps you manage a large number of connections from Lambda to an RDS database by establishing a warm connection pool to the database. Your Lambda functions interact with RDS Proxy instead of your database instance. It handles the connection pooling necessary for scaling many simultaneous connections created by concurrent Lambda functions. This allows your Lambda applications to reuse existing connections, rather than creating new connections for every function invocation.

Thus, the correct answer is: **Provision an RDS Proxy between the Lambda function and RDS database instance format**

