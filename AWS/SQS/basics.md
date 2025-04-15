- resised in public aws space. O any service having access to public aws zone can make use of it.
- HA withing a region
- messages polled are not deleted but hidden, if a client polls the message and then proceccese it, he needs to delete the message after the work is done explicitlly within the VisibilityTimeout frame otherwise the message reappears in the queue.
- after a long processes of not getting deleted again adn again, you can POSSIBLY move the message to DEAD-LEtter-QUEUE, which performs a different style of process on them..
- Queue has 2 componenet, one is used for adding elements to the queue, the other is responsible for reading it. and neither are connected, both are isolated of each other.

![[Pasted image 20250408195250.png]]



### An example of SQS in a simplified mannerism is:
![[Pasted image 20250408202927.png]]
- one part of the workload scaled out based on sqs, while the other part scales out when the user gives more load.

- one job is logged and generally multipme outputs are needed we use a more complicated version of it:
![[Pasted image 20250408203053.png]]

 this project overview is here: [[transcode using sqs Q]]


So why do we use this instead of the S3 event scheduler for lambda that we saw earlies? 
because object adding in S3 can generate only one event, but here we need to make 3 instances run seperately, for different resolutions. the sns here has 3 different SQS Qs subscribed to it, which works in a much efficient mannerism.

- ##### messages can stay up to 14 days in SQS queues


## Details:

![[Pasted image 20250408205146.png]]

- first, the **standard** is where you have to think it as a highway with multilane road or something, so it doesnt gives output all at once, or it might not even give after a long time. ALSO, This means duplicates **can happen**, so your application must be idempotent (able to handle the same message more than once safely).
- **FIFO**, think of it as a short term thing, where the lane in single lane, and Maintain the **order** of message delivery (First In, First Out). Also, if ALWAYS gives back a response.
- For **FIFO Queues**:
	- If you **batch messages together**, SQS can process up to **3,000 messages per second**.
	- If you send messages individually (no batching), it drops to **300 messages per second**.
- BUt for Standard, since its a multi lane, it takes more time to process that message.(i might be wrong, we will check)
- Billed for request:
	- here, one request is not equal to one message or anythign, IMPORTANT!!!
	- here, messages can be 0 as well, meaning the SQS have no message stored, but i will have to pay for the request that i made.
- Each request has: 
	- 1 to 10 messages at max
	- upto 256kb is the limit of the request, no matter the 1 to 10 messages.
- NOw, the timing of these requests:
	- if we are using the **short request** method, then the messages are being requested in short inntervals, becasue the request goes and fetches whatever is there and comes back instantaneously, as long as it fulfills the request limit (1-10 messages AND 256 kb max). If the SQS has no messages, then it still goes and checks, and for that request we are billed. Thus, it is expensive, because even for a single request with no messages involved we would have to keep checking and charged.
	- In **Long polling** request, there is a time interval, and in this time interval we wait up till the timee interval to wait for messages, and as soon as we have the **Request Limit reached**, we come back. And in case of the **Request LIMit** not reaching (1-10 messages, 256kb), then we wait till the time out happens and then come back. 
- Therefore, in short:
	- **Short Polling**:Immediately checks the queue and returns messages if available, even if **none are present**.This can result in **empty responses** and higher costs due to more requests.
	- **Long Polling**:Waits up to `waitTimeSeconds` (up to 20 seconds) **until a message is available**. Reduces **empty responses** and is more cost-efficient.
- Since messages are stored in messages, they need ti be encrypted at rest, done by server side, using AWS kms. And during trasnsfer, we use HTTPs/TLS for encryption at transit.
- Queue policy is similar to resource policy, wtih allowing or denying different accounts access mostly:
	- Who can send/receive messages.
	- Which services (like SNS) can publish messages to the queue.
- you can at the same time use IAM policies.

