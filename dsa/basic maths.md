String
- to change to string: String.valueOf(int i);
- or Integer.toString();
Then string to stringBuilder:
-  StringBuilder sb = new StringBuilder(strNum)

StringBuilder to String = .tostring();



---

dig=123
dig%10=3
dig/10=12

---


Integer.MIN_VALUE

---

![[Pasted image 20250424141123.png]]
prime or divisor


![[Pasted image 20250424141149.png]]
lets say our number is n=36
then 1 * 36
2 * 18
3 * 12
...
the if loop(n/i != i) is necessary for (6 * 6) to not be same. basically, not to print 6 two times.
print(i) gives us 1, 2, 3 and print(n/i) gives us 36, 18,12....
so that is why we need to check if (n/i != i)



---

prime number:
- a number which has exactly 2 factors. 1 and itself.

brute force:
- ![[Pasted image 20250424141429.png]]

optimal:
- ![[Pasted image 20250424171400.png]]
- basically, running thorugh sqrt of n numbers.
- check the square root method above to understand why there would be two count++

---

gcd

![[Pasted image 20250424173348.png]]

for 20, 40
we start from back only


or eucladian algo
![[Pasted image 20250424173458.png]]

optimiation of eucladean
![[Pasted image 20250424173616.png]]
![[Pasted image 20250424173633.png]]
![[Pasted image 20250424173655.png]]

![[Pasted image 20250424173706.png]]

