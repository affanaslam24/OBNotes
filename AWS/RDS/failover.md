### **Multi-AZ RDS Failover (for high availability)**

- **Write traffic:** Failover **automatically switches** the **primary (writer)** to the standby instance.
    
- **Read traffic:** The standby **cannot be used** for reads before or after failover — it's not accessible.
    
- **Endpoints:** The **same endpoint** (DNS) is preserved. AWS just remaps it to the new primary instance.
    

🧠 So you don’t need to change anything in the application.

---

### 🔹 **Read Replica Failover (for read scaling)**

- Read replicas are **asynchronous** and **read-only**.
    
- If the **primary RDS** fails, the read replica **does not** automatically take over.
    
- You must **manually promote** a read replica to become a standalone instance (and optionally reconfigure it as the new primary).
    
- After promotion, your **application must be updated** to point to the new writer endpoint.
    

---

### ✅ **Aurora’s Twist:**

Aurora handles this better.

- Aurora uses a **cluster endpoint model**:
    
    - `Cluster Endpoint`: Used for **writes**.
        
    - `Reader Endpoint`: Used for **read replicas** (load-balanced across replicas).
        
- Failover is **automatic**:
    
    - Aurora promotes a read replica to **writer** automatically (within seconds).
        
    - **Cluster endpoints** are automatically remapped — so **writes continue with the same endpoint**.
        

---

### 📝 Sample Exam Question:

**Q:** A company runs a Multi-AZ RDS PostgreSQL database for their production workload. How can the company ensure that both read and write traffic automatically switches to a healthy instance in the event of a failure?

**A:**  
✅ **Use Amazon Aurora with Multi-AZ and reader endpoints** to allow automatic failover for both read and write traffic without changing application configuration.