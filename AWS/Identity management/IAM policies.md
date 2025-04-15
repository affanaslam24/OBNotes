
managed policies, inline poliscies

aws managed policies, custom managed policies

deny alllow deny


**Q. can you make policies?** 
**yes, but check how.**

what are custom managed policies?

![[Screenshot from 2025-03-29 04-16-30.png]]
Make note, policies dont have principal. that mean, it signifies whatever is attached by the policies will have access to the actions and resources.

what does a po;icy have in it?
- Effect (allow or deny)
- action, the actions that we are authrosired to take basically.
- resoruces we are allowed to gain acess to.

The default, by implicit is deny. so any resource not mentioned is by defualt not given acess to us.
Then there is explicit deny and then expplicit allow.
the system goes something like this, you are not given access to anything, implicit deny, unless to ask for it, implicit allow, but if there is a specific deny on you, you cant acess some resources even if you are allowedacess.
deny allow deny.
chatgpt for better clarity in the statement.


Example:
![[Screenshot from 2025-03-29 04-17-17.png]]
sally, an iam identity, has 2 policy attached to it, and is part of a group which has one policy attached to it, and they are granted acess to a service in aws, but the service has a resource policy attached to it. Now, **always remember** we will see the whole deny allow deny and then find if sally will jhave acess to the service or not. if at an conjecture it was stateted that Sally has explicit deny to the service, she is not allowed to use it.


## what are managed policy?
well, we will need to see first, but what i can recall is its a compilation of various inlline policies.
![[Screenshot from 2025-03-29 04-18-15.png]]

instead of giving inline policies to each person, attach managed policies to identities. idk what this is, **so we need to check again**.

