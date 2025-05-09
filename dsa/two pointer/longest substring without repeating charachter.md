
s=cadbzabcd


there are various ways:
- first of all, we will use two pointers, and as we move forward we need to remmeber the concept of removing hte older elements when necessary.

We can do this in various ways:
- first, make an array with 256 space, becasue there are 256 charachters.
- or you can use hashMap to keep track of frequency of times a charachter comes, in that ways you get flexibility.
- OR you use hashset, because in hashSet, you only get one unique element isnide.

So, a hashSet, to check if the element is still there or not, then removing the elements when necessary, but we would be using while loop to remove this element as long as its inside the hashset.


![[Pasted image 20250507212321.png]]

There is one more way, where oyu dont shirnk the size of the box, and keep it going forward. well see how.



or instead of using a while loop to remove the characthers, we can use 
![[Pasted image 20250507212709.png]]
a map which stores the index of those elements.

![[Pasted image 20250507212903.png]]


![[Pasted image 20250507213028.png]]


