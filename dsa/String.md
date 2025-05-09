Outermost parenthesis:
![[Pasted image 20250508205825.png]]
or
Use stack:
![[Pasted image 20250508205907.png]]
- notice tgat you push the element later, 
- And you pop the element first, before checking the if conditions i means inside.


---

 String[] words = str.trim().split("\\s+");
how to make an array out of a string

---

From char to int:
- ch-'0'

---

how doe ssubsrting work:
String s = "abcdef";
System.out.println(s.substring(2));      // Output: "cdef"
System.out.println(s.substring(1, 4));   // Output: "bcd" (1 index to 3)
The result is a **new String** from `start` to `end - 1`.


String s = "hello";

// s.substring(0, 5) → "hello" ✅ entire string
// s.substring(5)    → ""       ✅ empty string
// s.substring(3, 3) → ""       ✅ empty string
// s.substring(3, 2) → ❌ throws IndexOutOfBoundsException

---

loargest odd number in a string:
![[Pasted image 20250508222529.png]]

---


Rotate 
![[Pasted image 20250508230810.png]]

or:
![[Pasted image 20250508230830.png]]


