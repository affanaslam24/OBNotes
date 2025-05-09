Great question! Understanding **compile time** vs **runtime** in Object-Oriented Programming (OOP) is crucial for grasping how Java (and many other languages) work under the hood.

---

### 🧠 **Compile Time vs Runtime in OOP**

|Aspect|Compile Time|Runtime|
|---|---|---|
|**Definition**|When the source code is translated into bytecode|When the program is actually executing|
|**Checked by**|The compiler|The Java Virtual Machine (JVM)|
|**Errors Caught**|Syntax errors, type checking, missing classes|NullPointer, ArrayIndexOutOfBounds, etc.|
|**Example Concept**|Method overloading|Method overriding (Dynamic Method Dispatch)|
|**Binding Type**|Static Binding|Dynamic Binding|

---

## ✅ **What Happens at Compile Time?**

The **Java compiler** checks:

- Class structure
    
- Data types
    
- Access modifiers
    
- Method signatures (for overloading)
    
- Variable declarations
    
- Syntax
    

### Example: **Method Overloading** (Compile-Time Polymorphism)

```java
class Calculator {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
}
```

Which `add()` method to call is decided **at compile time** based on argument types.

---

## ✅ **What Happens at Runtime?**

The **JVM** handles:

- Object creation (`new`)
    
- Method overriding resolution
    
- Memory allocation
    
- Exception handling
    
- Dynamic method dispatch
    

### Example: **Method Overriding** (Runtime Polymorphism)

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}
class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog(); // Reference of parent, object of child
        a.sound(); // Decided at runtime: prints "Dog barks"
    }
}
```

---

### 🔁 Summary

|OOP Concept|Compile Time or Runtime|
|---|---|
|Class declaration|Compile Time|
|Method overloading|Compile Time|
|Method overriding|Runtime|
|Constructor calls|Runtime|
|Object creation|Runtime|
|Dynamic dispatch|Runtime|
|Casting|Checked at Compile Time; may fail at Runtime|

---

Would you like a diagram or analogy for this difference?