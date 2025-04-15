![[Pasted image 20250408220955.png]]

- its real time.
- anytihng which requires real time sql based stream processing.

![[Pasted image 20250408221303.png]]
- the S3 bucket contains references, like the player name and metadata about them.
- the input stream contains their actual game informationusing there 2 we make the input which goes into processing and gives oiut output based on SQL query in the form of output stream.
- Any error forms an error stream table.
- Remeber, the processing is realtime, but if the output  stream is sent to kinesis firehose, it indirectly becomes **near realtime**




![[Pasted image 20250408221359.png]]
