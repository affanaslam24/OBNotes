


![[Pasted image 20250510015142.png]]
---

## 🔹 **Where Do We Use `super` in Java?**

|Usage|Purpose|When to Use|
|---|---|---|
|`super()`|Calls the parent class constructor|First line of a subclass constructor|
|`super(arguments)`|Calls a specific parent constructor with parameters|When the parent class doesn't have a default constructor|
|`super.methodName()`|Calls a method from the parent class (even if overridden)|When you want to use the parent’s version of the method|
|`super.variableName`|Accesses a field of the parent class|When it’s hidden by a field in the subclass|

---

### ✅ 1. **Calling Parent Constructor**

```java
class Animal {
    Animal(String name) {
        System.out.println("Animal constructor: " + name);
    }
}

class Dog extends Animal {
    Dog() {
        super("Dog"); // calls Animal(String name)
        System.out.println("Dog constructor");
    }
}
```

### ✅ 2. **Accessing Overridden Parent Method**

```java
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    void sound() {
        super.sound(); // calls Animal's sound()
        System.out.println("Dog barks");
    }
}
```

### ✅ 3. **Accessing Hidden Variables**

```java
class Animal {
    String type = "Animal";
}

class Dog extends Animal {
    String type = "Dog";

    void printTypes() {
        System.out.println(super.type); // prints "Animal"
        System.out.println(this.type);  // prints "Dog"
    }
}
```

---

## 🚫 Where `super` Cannot Be Used:

- In static contexts (`super` only works with instance members)
    
- To access grandparent class directly (`super.super` is not allowed)
    

---

## 🔁 Summary

|Use Case|Syntax|
|---|---|
|Call parent constructor|`super()` or `super(args)`|
|Call parent method|`super.methodName()`|
|Access parent field|`super.variableName`|

Would you like a code challenge to test your understanding of `super`?
