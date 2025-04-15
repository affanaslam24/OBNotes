![[Pasted image 20250408104304.png]]
- event batches- either everything is success or if a single event fails, the whole batch is considered faiiled.
- there is a 15 minute time out, so the event batch rpocessing needs to be done withing that time frame.
- it needs access to the source srvice. Execution role needs the permission to access it.

Asyncronous:
- since the source is the one sending the data, Lambda is not required to have permisiion for accessing the servcie. infat S3 shoulld have been configured in Lmabdas resource policy.
