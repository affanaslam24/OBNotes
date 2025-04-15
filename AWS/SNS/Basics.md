![[Pasted image 20250408124341.png]]

Architecture:
![[Pasted image 20250408124939.png]]

- there are producers
- there are subcsribers
- and some services can be both subscribers as well as peoducers.
- topic stays at the public aws zone.
- some services can use filters to filtr only relevant data.
- a common arch is when a single sns topic is connected to various sqs queues, this condition  is known as fanout architcture.
- where the topic fans out notifications to multiple SQS queues, and each SQS Queue can either perform same task or have different task allocted to it.
- and they work isolated to each othe.

![[Pasted image 20250408125407.png]]

