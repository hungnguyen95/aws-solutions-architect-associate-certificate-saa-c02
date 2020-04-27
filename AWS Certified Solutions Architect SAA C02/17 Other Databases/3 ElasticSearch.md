# 3. ElasticSearch

- Example: In DynamoDB, you can only find by primary key or indexes.
- With ElasticSearch, you can search **any field**, even partially matches
- It’s common to use ElasticSearch as a complement to another database
- ElasticSearch also has some usage for Big Data applications
- You can provision a cluster of instances
- Built-in integrations: Amazon Kinesis Data Firehose, AWS IoT, and Amazon CloudWatch Logs for data ingestion
- Security through Cognito & IAM, KMS encryption, SSL & VPC
- Comes with Kibana (visualization) & Logstash (log ingestion) – ELK stack

---

# ElasticSearch for Solutions Architect

- **Operations**: similar to RDS
- **Security**: Cognito, IAM, VPC, KMS, SSL
- **Reliability**: Multi-AZ, clustering
- **Performance**: based on ElasticSearch project (open source), petabyte scale
- **Cost**: pay per node provisioned (similar to RDS)
- **Remember: ElasticSearch = Search / Indexing**