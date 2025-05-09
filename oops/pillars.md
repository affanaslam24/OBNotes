The **four pillars of Object-Oriented Programming (OOP)** are the foundational principles that define how OOP works. They help in writing reusable, scalable, and maintainable code.

---

## 🧱 **1. Encapsulation**

**Definition:** Bundling data (variables) and methods that operate on that data into a single unit (class), and restricting access to some of the object's components.

- **Goal:** Hide internal state and require all interaction to be performed through an object’s methods.
    
- **Tool:** Access modifiers (`private`, `public`, `protected`).
    

```java
class Account {
    private double balance;

    public void deposit(double amount) {
        if (amount > 0) balance += amount;
    }

    public double getBalance() {
        return balance;
    }
}
```

---

## 👪 **2. Inheritance**

**Definition:** A mechanism where one class acquires the properties and behaviors (methods) of another class.

- **Goal:** Code reuse and logical hierarchy.
    
- **Keywords:** `extends` (for classes), `implements` (for interfaces).
    

```java
class Animal {
    void eat() { System.out.println("This animal eats food."); }
}

class Dog extends Animal {
    void bark() { System.out.println("Dog barks."); }
}
```

---

## 🎭 **3. Polymorphism**

**Definition:** The ability to present the same interface for different underlying data types.

- **Types:**
    
    - **Compile-time polymorphism (Method Overloading)**
        
    - **Runtime polymorphism (Method Overriding)**
        
- **Goal:** Flexibility in behavior depending on the object’s actual class.
    

```java
// Overriding
class Animal {
    void sound() { System.out.println("Animal makes sound"); }
}

class Dog extends Animal {
    void sound() { System.out.println("Dog barks"); }
}
```

---

## 🧩 **4. Abstraction**

**Definition:** Hiding complex implementation details and showing only essential features of the object.

- **Goal:** Focus on "what" an object does instead of "how" it does it.
    
- **Tools:** Abstract classes and interfaces.
    

```java
abstract class Vehicle {
    abstract void move();
}

class Car extends Vehicle {
    void move() { System.out.println("Car moves"); }
}
```

---

## ✅ Summary Table

|Pillar|What It Does|Tools Used|
|---|---|---|
|Encapsulation|Hides internal state|Private variables, public methods|
|Inheritance|Reuses code from other classes|`extends`, `implements`|
|Polymorphism|Allows one interface, many implementations|Overloading, Overriding|
|Abstraction|Shows essential features, hides implementation|Abstract classes, Interfaces|

Would you like real-world analogies for these pillars to help remember them better?