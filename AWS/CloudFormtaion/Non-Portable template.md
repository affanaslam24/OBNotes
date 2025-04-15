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

![[Pasted image 20250410132451.png]]

![[Pasted image 20250410132533.png]]
error becasue of the unique name issue
For chekcing the errors, check the events tap

![[Pasted image 20250410132711.png]]

- we can create as many stakcs from a single template, but name should be different of the stack.


Deleting a stack deletes the resources:
![[Pasted image 20250410132823.png]]



There can be various errors in templates:
![[Pasted image 20250410132946.png]]
this time the Ami image is not matching iwth the region ami image.


Therefore these are **non ppoortable tempplates**: meaning that there are restrictions to how many times you can appply the template, or how many regions it can work on.

 


--- 

