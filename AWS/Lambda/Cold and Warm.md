![[Pasted image 20250408104728.png]]
- so always remember that lambda functions are stateless. 
- any invocation, you have to assume will be a cold start no matter what.
- ofc there are ways to counter this
	- either make continuous invocstions, in which case the instance will be warm
	- or use provisioned concurrency.
- in case that the instance in warm, but you dont provide anything for its continual run, itll go back to terminate itslef, and lo beholld, a cold start will be at your hand again.
- if you want a persistent data to  be present at each invocation, you can have a temp file or storsge which is **OUTSIDE** of the lambda handler.
- this is because th each invocation runs the lambda function handler code, so the runtime is alwayus a new instance, and they run the code anew. But if you keep anything outside or configure resources outside, there are ways to perist data.

