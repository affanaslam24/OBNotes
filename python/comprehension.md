 a lil difficult to understand, but:

![[Pasted image 20250424210248.png]]

so what is happening is: there is a for loop, and by now we know that the for loop will print - 0,1,2,3,4

so what this comprehension does is, whatever the for loop prints, itll be as 'x', rihgt. because for 'x' in ....
And now see the left hand of the 'for', you can see an 'x'.
so what this 'x' does is, for every thing that the for lloop does, it adds it to the variable 'x'.

to understand much better:
![[Pasted image 20250424210514.png]]
for loop wouldve given values of x as = 0, 1, 2, 3, 4
and the x+5 does is 0+5, 1+5, 2+5...and add it to the list.



![[Pasted image 20250424210611.png]]


![[Pasted image 20250424210618.png]]


why did we add zeroes? its to show this:

![[Pasted image 20250424210710.png]]


so what this did was: there are 2 loops, one is what will be shown: a list of 100 zeroes.
and the other loop states how many number of elements will be there- 5.
in the example shown above, we have 5 lists of 100 zeroes each.

so what we understood was: (from this example-- x=[x for x in range(5)])
- what will be shown as elements (x)
- how many elements. (for x in range(5))


A much more comprehensive one:
![[Pasted image 20250424211002.png]]
if i%5 is 0, meaning only elements divisible by 5 can be printed in this range.

can add this to a dictionary:
![[Pasted image 20250424211114.png]]
like you can see, all the elements became keys 0, 5,10,15...

if you dont specify a ':' in between, like i:0 
![[Pasted image 20250424211218.png]]
you get a dictionary.

can create a tuple as well, but you will have to write 'tuple' otherwise itll create a 'generator' kind of object.


![[Pasted image 20250424211315.png]]

