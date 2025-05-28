Here's a complete and exam-friendly explanation of **MD5 vs SHA (Secure Hash Algorithm)** — covering the basics, key differences, vulnerabilities, and use cases:

---

## 🔐 MD5 vs SHA

Both **MD5** and **SHA** are **cryptographic hash functions** used to ensure **data integrity**, but they differ in strength, security, and modern use.

---

## 📌 1. What is MD5?

- **Full Form:** Message Digest Algorithm 5
    
- **Output Size:** 128-bit hash (32 hexadecimal characters)
    
- **Speed:** Fast
    
- **Security:** **Broken** – Vulnerable to **collision attacks**
    
- **Use Case (Legacy):** Checksums, old certificates, file verification (not secure anymore)
    

### ✅ Example:

```plaintext
MD5("hello") → 5d41402abc4b2a76b9719d911017c592
```

---

## 📌 2. What is SHA?

- **Full Form:** Secure Hash Algorithm
    
- **Versions:** SHA-1, SHA-2 (SHA-224, SHA-256, SHA-384, SHA-512), SHA-3
    
- **Output Size:**
    
    - SHA-1 → 160 bits (not secure)
        
    - SHA-256 → 256 bits (secure)
        
    - SHA-512 → 512 bits (secure)
        
- **Security:** SHA-2 and SHA-3 are **secure** (as of now)
    
- **Use Case:** Digital signatures, SSL/TLS, Bitcoin, HMAC, certificates
    

### ✅ Example (SHA-256):

```plaintext
SHA-256("hello") → 2cf24dba5fb0a30e26e83b2ac5b9e29e1...
```

---

## 📊 Comparison Table

|Feature|**MD5**|**SHA (e.g., SHA-256)**|
|---|---|---|
|**Full Form**|Message Digest 5|Secure Hash Algorithm|
|**Output Size**|128 bits|256+ bits (SHA-256, SHA-512, etc.)|
|**Security**|Weak (collision-prone)|SHA-2/SHA-3 are strong|
|**Speed**|Very fast|Slightly slower (but safer)|
|**Collision Resistance**|❌ Not resistant|✅ Resistant (SHA-2, SHA-3)|
|**Use Today?**|❌ No (only for non-security use)|✅ Yes (SHA-2/3 is widely used)|
|**Example Use Case**|File checksum (non-secure context)|Digital signatures, HTTPS, blockchain|

---

## ⚠️ Key Security Note:

- **MD5 and SHA-1 are deprecated** — do not use them for cryptographic security.
    
- Always prefer **SHA-256** or stronger (SHA-512, SHA-3).
    

---

## 🧠 Tip for Exams:

> **"MD5 is faster but weaker. SHA-2 is slower but secure. For real-world security, always choose SHA-2 or SHA-3."**

---

Let me know if you want a visual flowchart or MCQs for practice!

