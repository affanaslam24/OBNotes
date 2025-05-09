
- reverse an array:
![[Pasted image 20250424175304.png]]

using recursion:
![[Pasted image 20250424175338.png]]


---

- largest:
	- either use sorting
	- or take a variable named max, and then keep upating it.

always remember to use:
```java
large = Math.max(large,arr[i]);
```

---

- remove duplicate
![[Pasted image 20250504183926.png]]
![[Pasted image 20250504183950.png]]
OR
- you can do Hashset

---

- rotate left by one place
	- use a temp storsge for one place, and then do a[i]=a[i+1]\

---
- rotate by k places
	- reverse the 2nd half
	- then reverse the whole array
	- k%n to check soemthing sokmething, lets see.
![[Pasted image 20250504192746.png]]
revrev has the recursive reverse of array fucntion. its up there.
this was for left rotate.

- for right rotste
	- ![[Pasted image 20250504193330.png]]

1,2,3,4,5,6
k=2
output
6,5,1,2,3,4,5


---

- twoSum
![[Pasted image 20250505211550.png]]

- first sort, and then do the calculation. min....max
or

![[Pasted image 20250505211838.png]]


---


- union of a number:
1. make a hashmap, and then print all the keys.
2. make a hashsert, you wont have to set values.
3. using 2 pointers, one in each array:
	- if the numbers are same, print any one, required that it already doesnt exists in the arraylists last element.
	- if the numbers are different, check which one is bigger, and then add that one in the loist, but check if any of the number already exists or not.
	- this is how the while loop will run and end.
- if there still exists elements, itll be added using 2 seperate loops for each array.

---

- sorting 0s,1s,2s
![[Pasted image 20250506092215.png]]

![[Pasted image 20250506092416.png]]
![[Pasted image 20250506093841.png]]
- so what we udnetood was:
	- if mid is 0, exchange it with low, and move both mid and low.
	- if mid is 1, move mid by one
	- if mid is 2, exchange with high, and remove high to high-1.

---


majority element:

arr[2,2,1,1,2,2]

2 appears more than n/2 times, thats our answer.

- can use hashmap, and then check which has n/2 values to it.


- use moore algo:
	- count++ for the element check 
	- count-- for incorrect element
	- if the count =0 then new element and increase count to 1.
	- by running the algo, we get one elelemnt which MIGHT be the element w eneed
	- run a loop again and check if th eelement found in th efirst loop is indeed the n/2 greatest element.
---

Stock sums:

![[Pasted image 20250506105149.png]]![[Pasted image 20250506192331.png]]
we check the minimum before the sleected number, therefore if 6-1 is the highest profit, we move it to profiut.


---

next permutation:
![[Pasted image 20250506195154.png]]
