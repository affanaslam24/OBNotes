![[Pasted image 20250507113339.png]]


![[Pasted image 20250507113512.png]]



![[Pasted image 20250507113629.png]]



![[Pasted image 20250507113740.png]]

![[Pasted image 20250507113812.png]]



![[Pasted image 20250507113920.png]]


![[Pasted image 20250507114000.png]]


but it doesnt provides dynamic changing.

so useit with volyumeMounts.
instead of savimng thrm as env variables, save as files


![[Pasted image 20250507114310.png]]


![[Pasted image 20250507114327.png]]

![[Pasted image 20250507114336.png]]

![[Pasted image 20250507114357.png]]


you still have to write:
![[Pasted image 20250507114524.png]]

but it doesnt restarts the pod, it just matches the volume mounts this time



---


secrets:

![[Pasted image 20250507114656.png]]


![[Pasted image 20250507114729.png]]

![[Pasted image 20250507114738.png]]


![[Pasted image 20250507114758.png]]

its a basic encryption, you can provide your own key and algo