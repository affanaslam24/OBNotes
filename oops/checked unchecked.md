![[Pasted image 20250510020121.png]]
---

## ✅ **1. Compile-Time Exceptions (Checked Exceptions)**

These are **checked by the compiler** — if not handled properly, your code won’t compile.

### 🔧 Examples:

- `IOException`
    
- `SQLException`
    
- `FileNotFoundException`
    
- `ClassNotFoundException`
    

### 🔍 You **must** handle them using `try-catch` or declare them with `throws`.

```java
import java.io.*;

public class Test {
    public static void main(String[] args) throws IOException {
        FileReader fr = new FileReader("file.txt");  // Compile-time error if not handled
    }
}
```

---

## ✅ **2. Runtime Exceptions (Unchecked Exceptions)**

These occur **at runtime**, and are **not checked by the compiler**. Your code will compile even if you don’t handle them — but it may crash at runtime.

### 🔧 Examples:

- `NullPointerException`
    
- `ArrayIndexOutOfBoundsException`
    
- `ArithmeticException`
    
- `ClassCastException`
    

```java
public class Test {
    public static void main(String[] args) {
        int[] arr = new int[3];
        System.out.println(arr[5]);  // Runtime error: ArrayIndexOutOfBoundsException
    }
}
```

---

## 🧠 Summary Table:

|Aspect|Compile-Time Exception (Checked)|Runtime Exception (Unchecked)|
|---|---|---|
|Checked by compiler?|✅ Yes|❌ No|
|Must be handled?|✅ Yes|❌ No|
|When occurs?|Compile time|Runtime|
|Examples|`IOException`, `SQLException`|`NullPointerException`, `ArithmeticException`|

---

Would you like a tip on how to remember which is which?

