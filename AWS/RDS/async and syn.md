- multi az is synch
- readreplica is asynch



### **Synchronous Replication (used in Multi-AZ):**

- Data is **replicated in real-time** from the primary DB to the standby.
- The **primary waits** for acknowledgment from the secondary before confirming the write.
- Ensures **data consistency** and durability — both DBs are always in sync.
- **Used in Multi-AZ setups** for high availability.
📌 **Key Point:** If primary fails, standby can take over **with zero data loss**.


### **Asynchronous Replication (used in Read Replicas):**

- The primary DB does **not wait** for the replica to acknowledge writes.
- There is a **delay (replication lag)** — replica can be slightly behind.
- Improves performance by **offloading read traffic**, but not ideal for failover.
📌 **Key Point:** If primary fails, promoting a read replica may lead to **some data loss**.


FOR RDS

| Feature           | RDS Multi-AZ                | RDS Read Replica               |
| ----------------- | --------------------------- | ------------------------------ |
| Replication Type  | **Synchronous**             | **Asynchronous**               |
| Purpose           | High Availability           | Read Scaling, Offloading Reads |
| Replica Usability | Standby only (not readable) | Read-only and queryable        |
| Failover Support  | Automatic                   | Manual promotion needed        |
| Data Consistency  | Always in sync              | May lag behind                 |


## **How Aurora Does It Better**

Aurora takes the best of both and **re-engineers** it for cloud-native performance and resilience:

### ✅ **Storage is Decoupled and Shared**
- Aurora replicates data **6 times across 3 AZs** **at the storage layer**, not DB layer.
- Write once → distributed to storage nodes in parallel.
- This means: **no need for traditional standby or replication** logic!
### ✅ **Built-in High Availability (like Multi-AZ)**
- Aurora storage is always **multi-AZ** and fault-tolerant.
- If the writer fails, Aurora can **auto-promote a reader** from another AZ instantly.
### ✅ **Aurora Replicas (like Read Replicas, but better)**
- You can add **up to 15** Aurora Replicas.
- Replication is **ultra-fast** due to shared storage layer (not traditional async).
- **Failover to replica** is almost **instantaneous** and **lossless**.


|Feature|RDS Multi-AZ|RDS Read Replica|Aurora Cluster|
|---|---|---|---|
|Replication Type|Synchronous|Asynchronous|**Quorum-based + Shared Storage**|
|Use Case|High Availability|Read Scaling|Both (scaling + HA + auto failover)|
|Replica Usability|Not readable|Read-only|All replicas readable|
|Failover Type|Automatic|Manual (promotion)|Automatic (instant)|
|Max Replicas|1 standby|Up to 5|Up to 15 Aurora Replicas|
|Region Support|Single region|Cross-region possible|Cross-region with Global DBs (Aurora only)|


You can have both multi az and readreplica for an RDS.
Standby instances are only present in RDS, not in Aurora
AUrora is built it multi az.


