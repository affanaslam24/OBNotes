![[Pasted image 20250528000515.png]]

In the context of IPsec, DOI stands for ==Domain of Interpretation==. It's a document containing definitions for all the security parameters required for negotiating a VPN tunnel. Essentially, a DOI specifies the attributes needed for Security Association (SA) and Internet Key Exchange (IKE) negotiations.


---


SA (security association)
A **Security Association (SA)** is a **set of security parameters** that define how two network devices communicate securely.
A **Security Association** is a **logical connection** between two devices that defines **how data will be protected** during transmission—what encryption, authentication methods, keys, etc., will be use
it is like a contract that needs to be accepted by the entities.

![[Pasted image 20250528000929.png]]

---

mode of operation:
transport and tunnel mode:

![[Pasted image 20250528001257.png]]

tunnel:
- **Network-to-network** communication (e.g., between two routers or gateways).
- **VPNs** (Virtual Private Networks).
- Hides the **entire original IP packet**, including source/destination addresses.

transport:
- **Host-to-host** communication.
- When both endpoints are **end-user devices** (not routers or gateways).
- Faster but **less secure**, as headers are visible.
|   |
|---|
|**Example**|

|   |
|---|
|Router A ↔ Router B VPN|

|                             |
| --------------------------- |
| PC A ↔ PC B secure transfer |


---


authentication header:
![[Pasted image 20250528001943.png]]

![[Pasted image 20250528002035.png]]

![[Pasted image 20250528002104.png]]









![[Pasted image 20250525202638.png]]



![[Pasted image 20250525213652.png]]



ssl integrity and confidentialoity
![[Pasted image 20250525214734.png]]



ssl authentication:
![[Pasted image 20250525215119.png]]


![[Pasted image 20250525215320.png]]

