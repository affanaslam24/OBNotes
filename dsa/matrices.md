![[Pasted image 20250509133437.png]]
![[Pasted image 20250509133449.png]]
find a zero, and then make every zero in that row and column as zero

BUt only do this wiuth the initial zeroes, not with the ones who you make later on.


---

Brute forcE:
Instead of marking zeroes, mark the ones as -1:
![[Pasted image 20250509133705.png]]
![[Pasted image 20250509133833.png]]

look carefully at the row and column marking
look at the interchanging i and j in both. In one i is fixed, in the other j is fixed.


![[Pasted image 20250509134037.png]]

---

better solution:
![[Pasted image 20250509134259.png]]
first mark the col anf row:
![[Pasted image 20250509134332.png]]
And then run the matrix again, and if a row or a col is marked, idc you mark all the elements as 0:
![[Pasted image 20250509134414.png]]

----

Rotate by 90 degree:
![[Pasted image 20250509134802.png]]

![[Pasted image 20250509134830.png]]

![[Pasted image 20250509134846.png]]

![[Pasted image 20250509134906.png]]
look, the 'j' is same


And for the next common:
![[Pasted image 20250509134953.png]]
![[Pasted image 20250509135010.png]]
![[Pasted image 20250509135038.png]]


---

better solution:
First transpose, and then reverse:

![[Pasted image 20250509135203.png]]


### HOw to transpose:
 - The diagnols stay the same:
![[Pasted image 20250509135240.png]]

- Then you swap the elements on the diagnols:
![[Pasted image 20250509135336.png]]
![[Pasted image 20250509135414.png]]

Every index goes to opposite.


Important: 
We go till n-2 indeX:
![[Pasted image 20250509135452.png]]
![[Pasted image 20250509135504.png]]
And j is starting from i+1 and going till last

Then pick up every row and then reverse it:
![[Pasted image 20250509135540.png]]
![[Pasted image 20250509135610.png]]

Or use this reverse approach:
![[Pasted image 20250509135645.png]]


---


spiral:

![[Pasted image 20250509135818.png]]


![[Pasted image 20250509140023.png]]

![[Pasted image 20250509140115.png]]
left to right, right to bottom, bottom to left, left to top.

![[Pasted image 20250509140206.png]]

Rihgt:
![[Pasted image 20250509140238.png]]
remember to move top to one level down.

top to bottom:
![[Pasted image 20250509140313.png]]
Notice that the iteration is form top to bottom, but we are movingthe right index based.

And remember to remove right to one place keft:
![[Pasted image 20250509140406.png]]

NOw, right to left:;
![[Pasted image 20250509140425.png]]
the btton stays constant.

Nwo make sure the bottom goes one place up:
![[Pasted image 20250509140454.png]]
And then do bottom to top:
![[Pasted image 20250509140608.png]]
make sure the left moves ahead, for the next set of iteration.


![[Pasted image 20250509140628.png]]


---


trick between rows and columns:
![[Pasted image 20250509140724.png]]
number of columns is: mark the first row, and then find its size= [0].size()

number of rows: the number of elements isndie the matrix {{},{},{},{}} total of 4, that is your rows.


So the final loop will look llike this:
![[Pasted image 20250509140954.png]]

The while condition:
![[Pasted image 20250509141022.png]]

The siglle point of failurE:
![[Pasted image 20250509141120.png]]

Another condition:
![[Pasted image 20250509141143.png]]
