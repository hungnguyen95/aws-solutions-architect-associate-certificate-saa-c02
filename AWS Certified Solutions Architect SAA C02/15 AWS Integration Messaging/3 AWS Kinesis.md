# 3. AWS Kinesis

- **Kinesis** is a managed alternative to Apache Kafka
- Great for application logs, metrics, IoT, clickstreams
- Great for “real-time” big data
- Great for streaming processing frameworks (Spark, NiFi, etc…)
- Data is automatically replicated to 3 AZ

- **Kinesis Streams**: low latency streaming ingest at scale
- **Kinesis Analytics:** perform real-time analytics on streams using SQL
- **Kinesis Firehose**: load streams into S3, Redshift, ElasticSearch…

---

# Kinesis

![3%20AWS%20Kinesis/Untitled.png](3%20AWS%20Kinesis/Untitled.png)

- Process **Big Data** in real-time
- Real-time data will be put in Streams ⇒ Analytics (computed, pre-process data) ⇒ Store data (Firehose)

---

# Kinesis Streams Overview

- Streams are divided in ordered Shards / Partitions

![3%20AWS%20Kinesis/Untitled%201.png](3%20AWS%20Kinesis/Untitled%201.png)

- Data retention is 1 day by default, can go up to 7 days
- Ability to reprocess / replay data
- Multiple applications can consume the same stream
- Real-time processing with scale of throughput (add shard)
- Once data is inserted in Kinesis, it can’t be deleted (immutability)

---

# Kinesis Streams Shards

- One stream is made of many different shards
- 1MB/s or 1000 messages/s at write PER SHARD
- 2MB/s at read PER SHARD
- Billing is per shard provisioned, can have as many shards as you want
- Batching available or per message calls
- The number of shards can evolve over time (reshard / merge)
- **Records are ordered per shard**

![3%20AWS%20Kinesis/Untitled%202.png](3%20AWS%20Kinesis/Untitled%202.png)

---

# AWS Kinesis API – Put records

- PutRecord API + Partition key that gets hashed
- The same key goes to the same partition (helps with ordering for a specific key)
- Messages sent get a “sequence number”

    ⇒ Index length of shard after message is put

![3%20AWS%20Kinesis/Untitled%203.png](3%20AWS%20Kinesis/Untitled%203.png)

- Choose a partition key that is highly distributed (helps prevent “hot partition”)
    - user_id if many users
    - **Not** country_id if 90% of the users are in one country
- Use Batching with PutRecords to reduce costs and increase throughput
- **ProvisionedThroughputExceeded** if we go over the limits
- Can use CLI, AWS SDK, or producer libraries from various frameworks

---

# AWS Kinesis API – Exceptions

- ProvisionedThroughputExceeded Exceptions
    - Happens when sending more data (exceeding MB/s or TPS for any shard)
    - Make sure you don’t have a hot shard (such as your partition key is bad and too much data goes to that partition)

- Solution:
    - Retries with backoff
    - Increase shards (scaling)
    - Ensure your partition key is a good one

---

# AWS Kinesis API – Consumers

- Can use a normal consumer (CLI,SDK, etc…)
- Can use Kinesis Client Library (in Java, Node, Python, Ruby, .Net)
    - KCL uses DynamoDB to checkpoint offsets
    - KCL uses DynamoDB to track other workers and share the work amongst shards

![3%20AWS%20Kinesis/Untitled%204.png](3%20AWS%20Kinesis/Untitled%204.png)

---

# Kinesis Security

- Control access / authorization using IAM policies
- Encryption in flight using HTTPS endpoints
- Encryption at rest using KMS
- Possibility to encrypt / decrypt data client side (harder)
- VPC Endpoints available for Kinesis to access within VPC

---

# AWS Kinesis Data Firehose

- Fully Managed Service, no administration, automatic scaling, serverless
- Load data into Redshift / Amazon S3 / ElasticSearch / Splunk
- **Near Real Time**
    - 60 seconds latency minimum for non full batches
    - Or minimum 32 MB of data at a time
- Supports many data formats, conversions, transformations, compression
- Pay for the amount of data going through Firehose

---

# Kinesis Data Firehose Diagram

![3%20AWS%20Kinesis/Untitled%205.png](3%20AWS%20Kinesis/Untitled%205.png)

---

# Kinesis Data Streams vs Firehose

- Streams
    - Going to write custom code (producer / consumer)
    - Real time (~200 ms)
    - Must manage scaling (shard splitting / merging)
    - Data Storage for 1 to 7 days, replay capability, multi consumers
- Firehose
    - Fully managed, send to S3, Splunk, Redshift, ElasticSearch
    - Serverless data transformations with Lambda
    - **Near** real time (lowest buffer time is 1 minute)
    - Automated Scaling
    - No data storage

---

# Kinesis Data Analytics

![3%20AWS%20Kinesis/Untitled%206.png](3%20AWS%20Kinesis/Untitled%206.png)

- Perform real-time analytics on Kinesis Streams using SQL
- Kinesis Data Analytics:
    - Auto Scaling
    - Managed: no servers to provision
    - Continuous: real time
- Pay for actual consumption rate
- Can create streams out of the real-time queries