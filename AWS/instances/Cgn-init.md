##### Since we cant check whether the user data we gave works or not, what we can do is make usse of cfn init which is used inside cloudformation to check whether the user data was configured properly or not,

![[Screenshot from 2025-03-30 17-34-57.png]]


Rhis is the stack template:
![[Screenshot from 2025-03-30 17-36-58.png]]

It keeps a check while the stack is being built


![[Screenshot from 2025-03-30 17-38-43.png]]
it can give signals and has a timeout as well.


Steps:
The main config and userdata is inisde the metadata
the creationpolicy and signal is outside the metadata
the cfn init is making use inside the properties

![[Screenshot from 2025-03-30 17-39-39.png]]


metadata:
![[Screenshot from 2025-03-30 17-40-55.png]]
![[Screenshot from 2025-03-30 17-41-08.png]]
