# 3. DynamoDB

- Fully Managed, Highly available with replication across 3 AZ
- NoSQL database - not a relational database
- Scales to massive workloads, distributed database
- Millions of requests per seconds, trillions of row, 100s of TB of storage
- Fast and consistent in performance (low latency on retrieval)
- Integrated with IAM for security, authorization and administration
- Enables event driven programming with DynamoDB Streams
- Low cost and auto scaling capabilities

---

# DynamoDB - Basics

- DynamoDB is made of **tables**
- Each table has a **primary key** (must be decided at creation time)
- Each table can have an infinite number of items (= rows)
- Each item has **attributes** (can be added over time – can be null)
- Maximum size of a item is 400KB
- Data types supported are:
    - Scalar Types: String, Number, Binary, Boolean, Null
    - Document Types: List, Map
    - Set Types: String Set, Number Set, Binary Set

---

# DynamoDB – Provisioned Throughput

- Table must have provisioned read and write capacity units
- Read Capacity Units (RCU): throughput for reads ($0.00013 per RCU)
    - 1 RCU = 1 strongly consistent read of 4 KB per second
    - 1 RCU = 2 eventually consistent read of 4 KB per second
- Write Capacity Units (WCU): throughput for writes ($0.00065 per WCU)
    - 1 WCU = 1 write of 1 KB per second
- Option to setup auto-scaling of throughput to meet demand
- Throughput can be exceeded temporarily using “burst credit”
- If burst credit are empty, you’ll get a “ProvisionedThroughputException”.
- It’s then advised to do an exponential back-off retry

---

# DynamoDB - DAX

- DAX = DynamoDB Accelerator
- Seamless cache for DynamoDB, no application rewrite
- Writes go through DAX to DynamoDB
- Micro second latency for cached reads & queries
- Solves the Hot Key problem (too many reads)
- 5 minutes TTL for cache by default
- Up to 10 nodes in the cluster
- Multi AZ (3 nodes minimum recommended for production)
- Secure (Encryption at rest with KMS, VPC, IAM, CloudTrail…)

![3%20DynamoDB/Untitled.png](3%20DynamoDB/Untitled.png)

---

# DynamoDB Streams

- Changes in DynamoDB (Create, Update, Delete) can end up in a DynamoDB Stream

    ⇒ Any Create, Update, Delete will create a changelog (stream)

- This stream can be read by AWS Lambda, and we can then do:
    - React to changes in real time (welcome email to new users)
    - Analytics
    - Create derivative tables / views
    - Insert into ElasticSearch
- Could implement cross region replication using Streams
- Stream has 24 hours of data retention

![3%20DynamoDB/Untitled%201.png](3%20DynamoDB/Untitled%201.png)

---

# DynamoDB - New Features

- **Transactions (new from Nov 2018)**
    - All or nothing type of operations
    - Coordinated Insert, Update & Delete across multiple tables
    - Include up to 10 unique items or up to 4 MB of data
- **On Demand (new from Nov 2018)**
    - No capacity planning needed (WCU / RCU) – scales automatically
    - 2.5x more expensive than provisioned capacity (use with care)
    - Helpful when spikes are un-predictable or the application is very low throughput

---

# DynamoDB – Security & Other Features

- Security:
    - VPC Endpoints available to access DynamoDB without internet
    - Access fully controlled by IAM
    - Encryption at rest using KMS
    - Encryption in transit using SSL / TLS
- Backup and Restore feature available
    - Point in time restore like RDS
    - No performance impact
- Global Tables
    - Multi region, fully replicated, high performance
- Amazon DMS can be used to migrate to DynamoDB (from Mongo, Oracle, MySQL,S3, etc…)
- You can launch a local DynamoDB on your computer for development purposes

- **Global Tables:** (cross region replication)
    - Active replication, many regions
    - Must enable DynamoDB Streams
    - Useful for low latency, DR purposes

![3%20DynamoDB/Untitled%202.png](3%20DynamoDB/Untitled%202.png)

- **Capacity planning:**
    - Planned capacity: provision WCU & RCU, can enable auto scaling
    - On-demand capacity: get unlimited WCU & RCU, no throttle, more expensive