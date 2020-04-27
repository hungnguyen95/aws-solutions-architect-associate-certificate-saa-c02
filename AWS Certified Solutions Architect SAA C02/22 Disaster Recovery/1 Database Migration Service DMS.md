# 1. Database Migration Service (DMS)

- Quickly and securely migrate databases to AWS, resilient, self healing
- The source database remains available during the migration
- Supports:
    - Homogeneous migrations: ex Oracle to Oracle
    - Heterogeneous migrations: ex Microsoft SQL Server to Aurora
- Continuous Data Replication using CDC (Change Data Capture)
- You must create an EC2 instance to perform the replication tasks

![1%20Database%20Migration%20Service%20DMS/Untitled.png](1%20Database%20Migration%20Service%20DMS/Untitled.png)

---

# DMS Sources and Targets

**SOURCES**:

- On-Premise and EC2 instances databases: Oracle, MS SQL Server, MySQL, MariaDB, PostgreSQL, MongoDB, SAP, DB2
- Azure: Azure SQL Database
- Amazon RDS: all including Aurora
- Amazon S3

**TARGETS:**

- On-Premise and EC2 instances databases: Oracle, MS SQL Server, MySQL, MariaDB, PostgreSQL, SAP
- Amazon RDS
- Amazon Redshift
- Amazon DynamoDB
- Amazon S3
- ElasticSearch Service
- Kinesis Data Streams
- DocumentDB

---

# AWS Schema Conversion Tool (SCT)

- Convert your Database’s Schema from one engine to another
- Example OLTP: (SQL Server or Oracle) to MySQL, PostgreSQL, Aurora
- Example OLAP: (Teradata or Oracle) to Amazon Redshift

![1%20Database%20Migration%20Service%20DMS/Untitled%201.png](1%20Database%20Migration%20Service%20DMS/Untitled%201.png)

- **You do not need to use SCT if you are migrating the same DB engine**
    - Ex: On-Premise PostgreSQL => RDS PostgreSQL
    - The DB engine is still PostgreSQL (RDS is the platform)