![[Pasted image 20250410204253.png]]



![[Pasted image 20250410204551.png]]


![[Pasted image 20250410204937.png]]

- a custom resource is created which sends events to the lambda, and lambda sends back a response when the resource are done creating.

![[Pasted image 20250410205343.png]]
- the custom resource is lambda backed, meaning that its the one doing the extra work or something.


on the deletion process, lambda first removes the objects as per the event generated, and gives the response to ht estakc once the objects are deleted, then the stakc goes on to delete the custom resource, here bieng lambda, and then proceeds to delete the other resources.




![[Pasted image 20250410205650.png]]
![[Pasted image 20250410205807.png]]




The custom resource template, very complex
 ![[Screenshot from 2025-04-10 20-59-17.png]]
 ![[Screenshot from 2025-04-10 20-59-25.png]]


![[Pasted image 20250410210033.png]]



![[Pasted image 20250410210042.png]]




cusrom:
![[Pasted image 20250410210055.png]]



The responnse url
![[Pasted image 20250410210428.png]]



And all the other things:
![[Pasted image 20250410210551.png]]

the json:
![[Pasted image 20250410210601.png]]


