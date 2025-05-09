**Dynamic Method Dispatch** (also called **runtime polymorphism**) is a mechanism in Java where the **method to be called is determined at runtime**, not at compile time. It is used when a **parent class reference points to a child class object**, and the method that gets called is the **overridden version in the child class**, **not** the one in the parent.

---

### 🔧 How It Works:

When you do:

```java
Parent obj = new Child();
obj.work();  // Which method is called?
```

Even though `obj` is declared as type `Parent`, Java **looks at the actual object type (`Child`) at runtime** and calls `Child`’s `work()` method if it overrides the parent's.

---

### ✅ Example:

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
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
        Animal a = new Dog(); // Parent reference, child object
        a.sound();  // Output: Dog barks
    }
}
```

Even though `a` is an `Animal`, the actual object is a `Dog`, so `Dog`'s `sound()` method is called.

---

### 🔍 Key Points:

- Requires **inheritance**.
    
- Works with **method overriding**, not method overloading.
    
- Decision is made **at runtime**, hence "dynamic".
    
- Enables **polymorphism**, allowing for flexible and extensible code.
    

Would you like a memory diagram or analogy to understand this better?