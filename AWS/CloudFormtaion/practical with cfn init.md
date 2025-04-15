![[Pasted image 20250410194650.png]]

![[Pasted image 20250410194714.png]]
![[Pasted image 20250410194720.png]]
![[Pasted image 20250410194726.png]]
the user data method.
- so as you can see, there was a sleep of 5 mins, but the creation complete happened regardless of all the commands being run. 
Also, if we make changes to the parameters, it wont have any effect:
![[Pasted image 20250410195035.png]]
![[Pasted image 20250410195049.png]]
So a new instance will be created:
![[Pasted image 20250410195115.png]]

![[Pasted image 20250410195132.png]]
itll have a new ip adress.
![[Pasted image 20250410195155.png]]
**but there was no change to the content, because user data is only done once, even if the instance is created anew!!!**


----

using creation policy, signal

![[Pasted image 20250410195301.png]]
![[Pasted image 20250410195306.png]]

![[Pasted image 20250410195342.png]]
so this will tak time
it recieved the signal
![[Pasted image 20250410195352.png]]
![[Pasted image 20250410195406.png]]
and this will be uploaded.
**it still has the problem with, any updation to the user data will correspond to no change in the instance**


---

cfn init

![[Pasted image 20250410195703.png]]
![[Pasted image 20250410195715.png]]
- notice that there is no configset, there is only one configkey

Signal
![[Pasted image 20250410195905.png]]

To trpoubleshoot cfn init:
![[Pasted image 20250410195935.png]]
check the log files of cfn init.
![[Pasted image 20250410195953.png]]
![[Pasted image 20250410200009.png]]
shows the user data part
To see the whole config done:
![[Pasted image 20250410200048.png]]
the cfn-init-cmd.log
![[Pasted image 20250410200101.png]]

OR
![[Pasted image 20250410200133.png]]
![[Pasted image 20250410200138.png]]
gives you the actions that were performed, in sentence format.


-- still wont update when we do changes to the paramters of the cfn init configs.

---

cfn hub'

![[Pasted image 20250410200328.png]]

![[Pasted image 20250410200333.png]]
- what shiuld happen when an updation should occur
- ![[Pasted image 20250410200352.png]]
- this is the resource it will look at:
![[Pasted image 20250410200414.png]]
if the metadata changes in that resource:
![[Pasted image 20250410200435.png]]
this action will be taken

And if that happens, then this part of the metadata will be updated:
![[Pasted image 20250410200511.png]]

**NOTICE how the changes are done in the files tab of the config**.

And see the new log file inside the insance:
![[Pasted image 20250410200658.png]]
