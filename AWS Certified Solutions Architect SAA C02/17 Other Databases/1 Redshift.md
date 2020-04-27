# 1. Redshift

- Redshift is based on PostgreSQL, but **it’s not used for OLTP**
- **It’s OLAP – online analytical processing (analytics and data warehousing)**
- 10x better performance than other data warehouses, scale to PBs of data
- **Columnar** storage of data (instead of row based)
- Massively Parallel Query Execution (MPP), highly available
- Pay as you go based on the instances provisioned
- Has a SQL interface for performing the queries
- BI tools such as AWS Quicksight or Tableau integrate with it
- Data is loaded from S3, DynamoDB, DMS, other DBs…
- From 1 node to 128 nodes, up to 160 GB of space per node
- Leader node: for query planning, results aggregation
- Compute node: for performing the queries, send results to leader
- Redshift Spectrum: perform queries directly against S3 (no need to load)
- Backup & Restore, Security VPC / IAM / KMS, Monitoring
- Redshift Enhanced VPC Routing: COPY / UNLOAD goes through VPC

---

# Snapshots & DR

- Snapshots are point-in-time backups of a cluster, stored internally in S3
- Snapshots are incremental (only what has changed is saved)
- You can restore a snapshot into a **new cluster**
- Automated: every 8 hours, every 5 GB, or on a schedule. Set retention
- Manual: snapshot is retained until you delete it
- **You can configure Amazon Redshift to automatically copy snapshots (automated or manual) of a cluster to another AWS Region**

---

# Redshift Spectrum

- Query data that is already in S3 without loading it
- **Must have a Redshift cluster available to start the query**
- The query is then submitted to thousands of Redshift Spectrum nodes

![1%20Redshift/Untitled.png](1%20Redshift/Untitled.png)

---

# Redshift for Solutions Architect

- Operations: similar to RDS
- Security: IAM, VPC, KMS, SSL (similar to RDS)
- Reliability: highly available, auto healing features
- Performance: 10x performance vs other data warehousing, compression
- Cost: pay per node provisioned, 1/10th of the cost vs other warehouses
- **Remember: Redshift = Analytics / BI / Data Warehouse**