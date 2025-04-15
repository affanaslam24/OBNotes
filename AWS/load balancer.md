### **Key Features of AWS Load Balancer**

✅ **Health Checks** – Automatically removes unhealthy instances from routing.  
✅ **Auto Scaling Integration** – Works with Auto Scaling Groups to add/remove instances dynamically.  
✅ **SSL Termination** – Can handle HTTPS encryption/decryption, reducing server load.  
✅ **Sticky Sessions** – Ensures users connect to the same backend instance.  
✅ **Cross-Zone Load Balancing** – Distributes traffic across multiple Availability Zones.  
✅ **IP-based & Instance-based Routing** – Can route traffic to specific IPs, EC2 instances, or containers.


### **Where Does an AWS Load Balancer Run?**

- AWS automatically deploys **Load Balancer nodes** in **multiple Availability Zones**.
    
- These nodes distribute traffic across registered **targets** (EC2, Lambda, containers, etc.).
    
- You don’t see or manage these nodes—AWS handles everything in the background.