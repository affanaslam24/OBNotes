

![[loadyload.png]]

 These are all **advanced request-routing features of an Application Load Balancer (ALB)** in AWS. Let’s break them down one by one with **real-world examples** so you understand not only what they are but **why and when to use each**.

---

## 1. ✅ **Host-based Routing**

**👉 Route traffic based on the `Host` field in the HTTP request header.**

### 🔸 Example:

- A single ALB is handling multiple domains:
    
    - `shop.example.com`
        
    - `blog.example.com`
        

### 🔹 Use case:

- You want to send `shop.example.com` traffic to your shopping app.
    
- You want to send `blog.example.com` traffic to your blog app.

IF Host == "shop.example.com" → forward to Target Group A (shopping service)
IF Host == "blog.example.com" → forward to Target Group B (blog service)



## 2. ✅ **Path-based Routing**

**👉 Route traffic based on the URL path.**

### 🔸 Example:

- Single domain: `example.com`
    
- Routes based on URL paths:
    
    - `/cart`
        
    - `/admin`
        
    - `/products`
        

### 🔹 Use case:

- Send `/cart` to shopping cart microservice.
    
- Send `/admin` to admin backend.
    
- Send `/products` to product service.




## 3. ✅ **HTTP Header-based Routing**

**👉 Route traffic based on any standard/custom HTTP header.**

### 🔸 Example:

Client sends a custom header:


X-Environment: beta



## 4. ✅ **HTTP Method-based Routing**

**👉 Route traffic based on the HTTP method: GET, POST, PUT, DELETE, etc.**

### 🔸 Example:

- Your API `/orders` supports different actions:
    
    - `GET /orders` → fetch orders
        
    - `POST /orders` → create order
        

### 🔹 Use case:

- Route `POST` requests to one microservice (e.g., order creation service).
    
- Route `GET` requests to a read-optimized service.




## 5. ✅ **Query String Parameter-based Routing**

**👉 Route based on query parameters like `?version=2`**

### 🔸 Example:

- URL: `example.com/api?version=2`
    

### 🔹 Use case:

- Direct requests with `version=2` to a new version of your API.
- IF Query string "version" == "2" → Target Group B (v2 API)
ELSE → Target Group A (v1 API)



## 6. ✅ **Source IP Address CIDR-based Routing**

**👉 Route based on the client’s source IP or IP range.**

### 🔸 Example:

- Your company’s internal IP range: `192.168.0.0/16`
    
- Public users come from other IPs.
    

### 🔹 Use case:

- Route requests from internal IPs to an internal version of the app.
    
- Route public IPs to production app.



