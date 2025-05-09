![[Pasted image 20250426204415.png]]we can use these three ways to do things in html which the jinja2 template engine allows


like for this example:
![[Pasted image 20250425210255.png]]
we used {{}} to print output 

- now for the 'statements':
it can be any kind of statemnts: for statement, if conditions, etc

example:

![[Pasted image 20250426204516.png]]
also, make sure there is one space gap in between.


![[Pasted image 20250426204600.png]]

this way of checking in the html makes it very lightweight.

So, in our python code, and this is important, we will pass it as a dictionary:
![[Pasted image 20250426205056.png]]
that 'result=score' will need to change to 'result=exp'


Now, since we are using a dcitionary, we will need to iterate through it.
Therefore the new html file will look like this:

![[Pasted image 20250426205410.png]]
- and see how the statements and expressions are used concurrently together.


this will print it like this:
![[Pasted image 20250426205427.png]]


