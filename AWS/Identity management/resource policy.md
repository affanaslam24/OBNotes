
deny allow deny.
an anonymous principal will not have any policy, but an iam identity used having certain policies of itslf will be looked through.

first the resource policy is checked to see if the principal is allowed, and then the identity policy of the user is checked if they are allowed to use the resource or not.
eventually deny allow deny is worked.