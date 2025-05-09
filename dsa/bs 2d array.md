![[Pasted image 20250509141441.png]]
Easiest method:
![[Pasted image 20250509141507.png]]

optimisation:
convert the 1d coordinate to 2d coordinate:
![[Pasted image 20250509141721.png]]
row=index/m
column=index%m

So the solution is:
![[Pasted image 20250509141921.png]]







----



![[Pasted image 20250509115832.png]]
For this solution we can also use this method, of finding buianey searhc in each row:
![[Pasted image 20250509142126.png]]


we start from row 0, end at column last.

---


what is going to be the column?
![[Pasted image 20250509120124.png]]
![[Pasted image 20250509120133.png]]


---


![[Pasted image 20250509120249.png]]

![[Pasted image 20250509120315.png]]

column-- is  the reduction of column from the right hand side.
And increment of row means increasing downward.


---


In a sorted matric:
![[Pasted image 20250509120511.png]]

![[Pasted image 20250509120616.png]]

![[Pasted image 20250509120650.png]]

![[Pasted image 20250509120719.png]]

our bounds


![[Pasted image 20250509120839.png]]

![[Pasted image 20250509120907.png]]
rstart and rend, see this in chatgpt once.


![[Pasted image 20250509121111.png]]

Finditng the column in which we are going to do our search

![[Pasted image 20250509121253.png]]

![[Pasted image 20250509121349.png]]

![[Pasted image 20250509121428.png]]

