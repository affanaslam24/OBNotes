- KInses is not the same as SQS quesues. **make note of this**.
- And in exam you will be made sure to confuse between the two. [[AWS/SQS/basics|So read the basics of SQS properly]].  
- Also, refer to the difference: [[SQS and kinesis difference]]
- Data can be stored for 24hr, and new data can be stored at 24 hr later
- and each consumer accessing the data can have different request rate, some accessing it each minute, some each hour, or some only once or twice throughtout the 24hrs.
- ![[Pasted image 20250408212239.png]]



### Understanding the arch:

![[Pasted image 20250408212548.png]]
- there is a producer that creates the streams. and the consumers that use this data.
- the window is 24hr long, but can be extended upto 7 days with extra charges. This window is basically data persistance for the time frame. Aftr that newer data is added and the older data gets removed.
- the Stream has shards. (those 1,2...N are the shards)
- each shard can an igestion rate of 1MB per second, and consumption (output speed) of 2MB per second.
- the more shards a stream has, the more expensive it is, the better performance it will provide, the more data is being stored to it.
- how are data stored in shards? its in linear format, as the data is being ingested to it.
- Now, since the persistance of data is within 24hrs to 7 days, but you want to save it for more time, then you can transfer this data to AWS.
- And for this transfer, you can use a service like **kinesis Firehose**, which sents bulk of data to a service rather than letting it process.
