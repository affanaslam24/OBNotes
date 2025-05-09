A weather forecast agency collects key weather metrics across multiple cities in the US and sends this data in the form of key-value pairs to AWS Cloud at a one-minute frequency.

As a solutions architect, which of the following AWS services would you use to build a solution for processing and then reliably storing this data with high availability? (Select two)



**AWS Lambda**

With AWS Lambda, you can run code without provisioning or managing servers. You pay only for the compute time that you consume—there’s no charge when your code isn’t running. You can run code for virtually any type of application or backend service—all with zero administration.

**Amazon DynamoDB**

Amazon DynamoDB is a key-value and document database that delivers single-digit millisecond performance at any scale. It's a fully managed, multi-region, multi-master, durable database with built-in security, backup and restore, and in-memory caching for internet-scale applications. Amazon DynamoDB is a NoSQL database and it's best suited to store data in key-value pairs.

AWS Lambda can be combined with DynamoDB to process and capture the key-value data from the IoT sources described in the use-case. So both these options are correct.

Incorrect options:

**Amazon Redshift** - Amazon Redshift is a fully-managed petabyte-scale cloud-based data warehouse product designed for large scale data set storage and analysis. You cannot use Redshift to capture data in key-value pairs from the IoT sources, so this option is not correct.

**Amazon ElastiCache** - Amazon ElastiCache allows you to seamlessly set up, run, and scale popular open-Source compatible in-memory data stores in the cloud. Build data-intensive apps or boost the performance of your existing databases by retrieving data from high throughput and low latency in-memory data stores. Amazon ElastiCache is a popular choice for real-time use cases like Caching, Session Stores, Gaming, Geospatial Services, Real-Time Analytics, and Queuing. Elasticache is used as a caching layer in front of relational databases. It is not a good fit to store data in key-value pairs from the IoT sources, so this option is not correct.

**Amazon RDS** - Amazon Relational Database Service (Amazon RDS) makes it easy to set up, operate, and scale a relational database in the cloud. It provides cost-efficient and resizable capacity while automating time-consuming administration tasks such as hardware provisioning, database setup, patching, and backups. Relational databases are not a good fit to store data in key-value pairs, so this option is not correct.

----


----


----


Great question — Redshift and DynamoDB are often used **together** when you need **fast operational storage** (DynamoDB) and **analytical processing** (Redshift). Here's how they work together:

---

### 🔹 Use Case:

- You store real-time or high-throughput data in **DynamoDB** (e.g., user activity, IoT data).
    
- You need to **analyze** that data using **complex SQL**, **joins**, **aggregations**, or integrate with other datasets — that's where **Redshift** comes in.
    

---

### 🔸 **There are two main ways Redshift integrates with DynamoDB:**

#### 1. **Redshift COPY command to import from DynamoDB**

- Redshift has a built-in **`COPY` command** that supports loading data **directly from a DynamoDB table** into Redshift.
    
- You can **run periodic batch loads** for analysis.
    

```sql
COPY my_redshift_table
FROM 'dynamodb://my_dynamodb_table'
IAM_ROLE 'arn:aws:iam::1234567890:role/MyRedshiftRole'
REGION 'us-east-1';
```

✅ Use this for:

- Ingesting historical data for analytics.
    
- Joining DynamoDB data with other tables in Redshift.
    

---

#### 2. **Using AWS Glue (ETL) between DynamoDB and Redshift**

- AWS Glue can **extract data from DynamoDB**, **transform it**, and **load it into Redshift**.
    
- This gives you more flexibility to **clean, enrich, or format** data before analysis.
    

✅ Use this when:

- You want to process large datasets.
    
- You need transformations before loading into Redshift.
    

---

### 🔹 Example Architecture:

```
DynamoDB (real-time data) 
       ↓
  [Glue or COPY]
       ↓
Amazon Redshift (analytics, dashboards, SQL)
```

---

### 🧠 TL;DR:

- **DynamoDB** = fast operational NoSQL DB.
    
- **Redshift** = powerful SQL analytics engine.
    
- Use **COPY** or **AWS Glue** to bring data from DynamoDB into Redshift for analytics.
    

Want help with writing the `COPY` command or designing the ETL with Glue?

