A **Spot Fleet** in AWS is a way to **launch and manage a collection of Spot Instances** (and optionally On-Demand Instances) to meet a specific **target capacity** and **lowest possible cost** using a mix of instance types and Availability Zones.

A **Spot Fleet**:

- Is like a **strategic group of EC2 instances**.
- Uses a **Spot Fleet Request** that tells AWS:
    - What instance types you’re okay with
    - How many vCPUs or instances you want
    - Your max price (optional)
    - Whether you're open to using On-Demand instances if Spot is not available

### Why Use a Spot Fleet?

**Spot Instances** are up to **90% cheaper** than On-Demand, but:
- They can be **interrupted** at 2 minutes' notice if AWS needs the capacity back.
- Availability is **not guaranteed**.

So instead of manually trying to find which Spot Instances are cheap and available, Spot Fleet **automates** this.



|Component|Description|
|---|---|
|**Target Capacity**|The amount of compute power you want (can be by instance count or vCPU units).|
|**Launch Specifications**|The instance types, AMIs, subnets, etc., you're okay with.|
|**Allocation Strategy**|How AWS chooses instances: `lowestPrice`, `capacityOptimized`, or `diversified`.|
|**Instance Types**|You can give multiple types (e.g., `m5.large`, `c5.large`, `t3.medium`).|
|**Mix with On-Demand**|Optionally include On-Demand to increase reliability.|


A big data app (like Spark or Hadoop) needs 500 vCPUs for processing:

- You submit a Spot Fleet request for 500 vCPUs.
- You allow `m5.large`, `c5.large`, and `r5.large` as instance types.
- AWS finds the cheapest mix of Spot Instances across AZs and types to satisfy your request.

---


difference between spot instance and spot fleet:

### **Spot Instances**

- **Single Instance**: A **Spot Instance** refers to an individual EC2 instance that you request and run using **Spot pricing**.
    
- **Manual Management**: You request a specific **instance type**, **region**, and **availability zone** for that individual instance.
    
- **Bid Price**: You specify the **maximum price** you're willing to pay per hour for that instance. If your bid exceeds the current Spot price, the instance will run until AWS needs that capacity back.
    
- **Less Flexibility**: If the instance is interrupted (because AWS needs to reclaim capacity), you need to manage the interruption yourself, possibly by launching another instance.



SPOT FLEET:
- **Group of Instances**: A **Spot Fleet** is essentially an **automated group of EC2 instances**, where you can combine multiple Spot Instances (and optionally On-Demand Instances) to meet a target capacity (in terms of **instance count** or **vCPUs**).
    
- **Automatic Scaling and Diversification**: Spot Fleet automatically manages the lifecycle of your Spot Instances, scaling in and out based on the available capacity and your requirements. It also allows you to **diversify** the selection of instance types and availability zones.
    
- **Allocation Strategy**: Spot Fleet provides different allocation strategies, such as:
    
    - **`lowestPrice`**: Automatically chooses the cheapest available Spot Instance pools.
        
    - **`capacityOptimized`**: Chooses the Spot pools that have the highest available capacity.
        
    - **`diversified`**: Spread your instances across multiple pools for higher availability.
        
- **Fault Tolerance**: Spot Fleet can **automatically replace interrupted instances** by launching new instances, based on the capacity you need. This reduces downtime.
    
- **Ease of Management**: Instead of manually managing multiple individual Spot Instances, Spot Fleet automates the entire process, including instance selection, scaling, and handling interruptions



### **Example Use Cases**

- **Spot Instance**:
    
    - You might use a **Spot Instance** for a single, long-running batch job where cost savings are crucial and the application can tolerate interruptions (e.g., rendering video files).
        
- **Spot Fleet**:
    
    - You might use **Spot Fleet** for a **scalable web application** that needs to handle dynamic load. The fleet will automatically scale up and down, replace interrupted instances, and diversify across multiple instance types and AZs to ensure higher availability.



---


Keynotes:


in spot fleet, lets say an instance goes down due to the pricing thing of aws or whatever, will a new spot instance be replace3d in its place?
- Yes, in a **Spot Fleet**, if a Spot Instance is interrupted (e.g., due to price fluctuations, capacity unavailability, or other reasons), **Spot Fleet** can automatically replace that instance with a new Spot Instance.
- **Monitoring**:
- Automatic replacement
- replacement strategy
- scaling
that is the process


### **Spot Fleet and On-Demand Instances**:

In a **Spot Fleet**, you can **mix and match Spot Instances with On-Demand Instances**. This provides flexibility and helps you ensure high availability while keeping costs down.

For example:

- If your Spot Instances are interrupted, you can have **On-Demand Instances** in your Spot Fleet to fill in the gap and maintain the desired capacity.
    
- **On-Demand Instances** will not be interrupted, but they will cost more, so they are usually used in combination with Spot Instances to provide stability for workloads that need high availability.



----

---

---


The Spot Fleet selects the Spot Instance pools that meet your needs and launches Spot Instances to meet the target capacity for the fleet. By default, Spot Fleets are set to maintain target capacity by launching replacement instances after Spot Instances in the fleet are terminated.

A Spot Instance is an unused Amazon EC2 instance that is available for less than the On-Demand price. Spot Instances provide great cost efficiency, but we need to select an instance type in advance. In this case, we want to use the most cost-optimal option and leave the selection of the cheapest spot instance to a Spot Fleet request, which can be optimized with the `lowestPrice` strategy. So this is the correct option.

Key Spot Instance Concepts:

![](https://assets-pt.media.datacumulus.com/aws-saa-pt/assets/pt2-q49-i1.jpg)

via - [https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html)

Incorrect options:

**Run the workload on Spot Instances** - A Spot Instance is an unused Amazon EC2 instance that is available for less than the On-Demand price. Because Spot Instances enable you to request unused Amazon EC2 instances at steep discounts, you can lower your Amazon EC2 costs significantly. The hourly price for a Spot Instance is called a Spot price. Only spot fleets can maintain target capacity by launching replacement instances after Spot Instances in the fleet are terminated, so spot instances, by themselves, are not the right fit for this use-case.

**Run the workload on Reserved Instances (RI)** - Reserved Instances are less cost-optimized than Spot Instances, and most efficient when used continuously. Here the workload is once a month, so this is not efficient.

**Run the workload on Dedicated Hosts** - Amazon EC2 Dedicated Hosts allow you to use your eligible software licenses from vendors such as Microsoft and Oracle on Amazon EC2 so that you get the flexibility and cost-effectiveness of using your licenses, but with the resiliency, simplicity, and elasticity of AWS. An Amazon EC2 Dedicated Host is a physical server fully dedicated for your use, so you can help address corporate compliance requirement. They're not particularly cost-efficient. So this option is not correct.

References:

[https://docs.aws.am](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html)
