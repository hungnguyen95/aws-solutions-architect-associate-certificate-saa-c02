# 2. Neptune

- Fully managed **graph** database
- **When do we use Graphs?**
    - High relationship data
    - Social Networking: Users friends with Users, replied to comment on post of user and likes other comments.
    - Knowledge graphs (Wikipedia)
- Highly available across 3 AZ, with up to 15 read replicas
- Point-in-time recovery, continuous backup to Amazon S3
- Support for KMS encryption at rest + HTTPS

![2%20Neptune/Untitled.png](2%20Neptune/Untitled.png)

---

# Neptune for Solutions Architect

- **Operations**: similar to RDS
- **Security**: IAM, VPC, KMS, SSL (similar to RDS) + IAM Authentication
- **Reliability**: Multi-AZ, clustering
- **Performance**: best suited for graphs, clustering to improve performance
- **Cost**: pay per node provisioned (similar to RDS)
- **Remember: Neptune = Graphs**