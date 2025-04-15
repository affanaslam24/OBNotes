![[Screenshot from 2025-03-30 15-00-08.png]]
- The data is encrypted nd then stored in the volume. 
- the DEK is kept at the EC2 hosts, and whenever the instance wants to access the volume, the key is used to decrypt it and then gets inside the instance.
- **I Dont know what the other guy with PLAINEXT At REST is showing?**
- Q. is it th cmk or the dek stored in the EC2? id say the DEK.
- or maybe the instance asks for the CMK? idk. check

![[Screenshot from 2025-03-30 15-00-43.png]]
- The snapshots stored are also encrypted with the same DEK.

![[Screenshot from 2025-03-30 15-01-27.png]]

- the OS is never aware of the encryption, IMPORTANT.
- can you change the encryption  option later? nopes.
- one unique DEK per volume.
- Account can use a default CMK to use, or can have a specific CMK chosed by us.

