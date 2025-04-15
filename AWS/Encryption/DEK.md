CMK had a lot of issues of itself, like the 4kb probelm and the fact that it cant leave the kms.

so counter all that we introduced DEK
![[Screenshot from 2025-03-29 16-47-13.png]]

So we have the DEK in the plaintext format, which is then encrypted usiing the CMK inside the kms.
We use the DEK of plaintext to encrypt our data, and then we DISCARD the plaintext key.
We store the Encrypted DEK with the data, whenever we need to accesss the document in decrypted format, we ask the kms to decrypt.
How does kms get involved? SInce the CMK still exists, it automatically knows which CMK was used to encrypt the DEK in the data, and it decrypts the DEK. The decrypted DEK is then used for decryption of the data.

### KEY Notes

![[Screenshot from 2025-03-29 16-49-06.png]]
******They are region based************


IMPORTANT:
![[Screenshot from 2025-03-29 16-50-18.png]]

Keys have their own policy (resource policy)
And the iAM policy that are for users and roles.
NEED to do more reasearch on this.

BUT carefully look at the key policy where the PRincipal is written over there. It has only one account, and its giving root user the only acess.

![[Screenshot from 2025-03-29 16-50-36.png]]

the other one might bet the  iam policy


We need to folow the course outlet to see how the key policy looks like.


To understand how this is configured we need to look at the actual thing:
![[Screenshot from 2025-03-29 16-52-30.png]]
you cant see it but this is the administer level acess to the keys. basically who can make changes to the keys.

And then we select the key policies.
![[Screenshot from 2025-03-29 16-52-40.png]]
 basically which users or roles can acess this key. who can use it.

Understand that both these are different. one grants access to make changes to the key and the other gives access to make use of the keys.

THe permission looks something like this:

![[Screenshot from 2025-03-29 16-53-06.png]]
![[Screenshot from 2025-03-29 16-53-32.png]]
![[Screenshot from 2025-03-29 16-53-38.png]]
make note that all of these are in the same policy.


# How to use the key
![[Screenshot from 2025-03-29 17-05-44.png]]
to encrypt

![[Screenshot from 2025-03-29 17-06-20.png]]
to decrypt

