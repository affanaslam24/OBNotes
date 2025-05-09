### 🔄 Multithreading in Java (With Example)

---

## 🧠 **What is Multithreading?**

Multithreading is a feature that allows **multiple threads to run concurrently** in a single program. It's useful for performing **multiple tasks at the same time**, improving performance and responsiveness (especially in I/O-heavy applications).

---

## ✅ **Basic Terms**:

- **Thread**: A lightweight sub-process, the smallest unit of processing.
    
- **Main thread**: The thread which runs your `main()` method.
    
- **Concurrency**: Multiple tasks making progress at the same time.
    

---

## 🔧 **Creating Threads in Java** (2 ways):

### **1. Extending the Thread class**

```java
class MyThread extends Thread {
    public void run() {
        for (int i = 1; i <= 5; i++) {
            System.out.println("From MyThread: " + i);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();  // Thread created
        t1.start();                    // Thread started

        for (int i = 1; i <= 5; i++) {
            System.out.println("From main: " + i);
        }
    }
}
```

---

### **2. Implementing Runnable Interface**

```java
class MyRunnable implements Runnable {
    public void run() {
        for (int i = 1; i <= 5; i++) {
            System.out.println("From Runnable: " + i);
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Thread t1 = new Thread(new MyRunnable());
        t1.start();

        for (int i = 1; i <= 5; i++) {
            System.out.println("From main: " + i);
        }
    }
}
```

---

## 🕹️ **Output (varies each time):**

```
From main: 1
From Runnable: 1
From main: 2
From Runnable: 2
...
```

> Output order is **non-deterministic** because both threads run **concurrently**.

---

## 🧠 Key Concepts in Multithreading:

|Concept|Description|
|---|---|
|`start()`|Starts the thread and calls `run()`|
|`run()`|Defines the code that runs in the thread|
|`sleep(ms)`|Pauses thread for specified milliseconds|
|`join()`|Waits for another thread to finish|
|`synchronized`|Keyword used to prevent thread interference|
|`Thread.currentThread()`|Returns the currently running thread|

---

## ⚠️ Why Multithreading?

- Run heavy tasks in background (like file download)
    
- Improve CPU utilization
    
- Faster execution (especially with multiple cores)
    

---

Would you like an example with synchronization or real-life analogy?
