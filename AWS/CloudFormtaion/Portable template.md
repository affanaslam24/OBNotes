
#### 1.  nonportable:

Resources:
	Bucket:
		Type: 'AWS::S3::Bucket'
		 Properties:
			 BucketName: 'nameeeeeeeunique'
	 Instance:
		 Type: 'AWS::EC2::Instance'
		 Properties:
			 KeyName: 'A4L'
			 IsnanceType: ....
			 ImageId: '.....'

---

#### 2. portable stage 1:

![[Pasted image 20250410145411.png]]
- we removed the dependency on the name, but this then generates a random name
- we still havent configured the keyname dependency and the image dependency.
- ![[Pasted image 20250410145750.png]]


---
#### Stage2:



![[Pasted image 20250410145828.png]]
It uses paramters
- but this is hardcoded.
![[Pasted image 20250410145912.png]]
notice that the **TYPE** is aws service.
So it will show us this:
![[Pasted image 20250410145942.png]]
a selection option.


 ---
#### Stage 3:

![[Pasted image 20250410150218.png]]
- we removed the key pair, because there are iother option for connection, like insgtance connect over here.


![[Pasted image 20250410150241.png]]


See, autopopulates, from the parameter store. Dynamic reference
- Basically SSm parameter store gives us AWS managed things which changes based on environment and etc, dynamically.


---

keyn9tess:
- have as less parameters as possible.
- try not to name your resources, becaus ethat limits its stack creation


