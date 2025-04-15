![[Pasted image 20250403010822.png]]

Now the 2nd last one where a check grace period is set, is very important, becaude yoou need to make the health check wait for until your system is launched with the required bootstrap, if configured any, to load. 
in exam you can het a question where the systems health check keeps cradhing, and its quite possible its because the health check is checking earlier than the requred bootstraping to privison. so youu need to be aware of how long it takes for your syetem to bootstrap.

**Also, in the same context, we need to gind out what and when does the whole instance br3aking like this can happen. i mean, in lifecucle hooks we saw condiiones which can suspend an instance and then we have simialr cases in scaling processes, certain conditions as such. so research in chatgpt about this.**

