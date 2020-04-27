# 4. Aurora

- Aurora is a proprietary technology from AWS (not open sourced)
- Postgres and MySQL are both supported as Aurora DB (that means your drivers will work as if Aurora was a Postgres or MySQL database)
- Aurora is “AWS cloud optimized” and claims 5x performance improvement over MySQL on RDS, over 3x the performance of Postgres on RDS
- Aurora storage automatically grows in increments of 10GB, up to 64 TB
- Aurora can have 15 replicas while MySQL has 5, and the replication process is faster (sub 10ms replica lag)
- Failover in Aurora is instantaneous. It’s HA (High Availability) native.

    → it's going to be much faster than a failover from Multi-AZ on MySQL on RDS

- Aurora costs more than RDS (20% more) – but is more efficient

---

# High Availability and Read Scaling

- 6 copies of your data across 3 AZ:
    - 4 copies out of 6 needed for writes
    - 3 copies out of 6 need for reads
    - Self healing with peer-to-peer replication

        If some data is corrupted or bad, then it does self healing with peer-to-peer replication in the back end

    - Storage is striped across 100s of volumes

![4%20Aurora/Untitled.png](4%20Aurora/Untitled.png)

- If you were to write some data, maybe blue data, orange data, green data, you'll see 6 copies of it in 3 different AZs. The cool things is that it goes on different volumes, and it's striped, and it works really really well.
- Aurora is like multi AZ for RDS ⇒ One Aurora Instance takes writes (master)

![4%20Aurora/Untitled%201.png](4%20Aurora/Untitled%201.png)

- If the master doesn't work, automated failover for master in less than 30 seconds
- Master + up to 15 Aurora Read Replicas serve reads

![4%20Aurora/Untitled%202.png](4%20Aurora/Untitled%202.png)

- Any of these Replicas can be become the master, in case the master fails
- **Support for Cross Region Replication**

---

# Aurora DB Cluster

![4%20Aurora/Untitled%203.png](4%20Aurora/Untitled%203.png)

- We have a shared volume storage and it's auto expanding from 10GB to 64TB
- Master is the only thing that will write to your storage.
    - Because the Master can change and failover, Aurora provides you a Writer Endpoint. It's a DNS name (Writer Endpoint)
    - Even if the master fails over, your client still talks to the Writer Endpoint and it is automatically redirected to the right instance
- You can have auto scaling on top of these Read Replicas
    - You can have 1 up to 15 Read Replicas
    - You can setup auto scaling, such as you always have the right number of Read Replicas
    - You have a Reader Endpoint ⇒ It has the exact same feature as a Writer Endpoint
    - It helps with connection load balancing, and it connects automatically to all the Read Replicas
    - Anytime the client connects to the Reader Endpoint, it will get connected to one of the Read Replicas and it will load balancing done this way

    ---

    # Features of Aurora

    - Automatic fail-over
    - Backup and Recovery
    - Isolation and security
    - Industry compliance
    - Push-button scaling
    - Automated Patching with Zero Downtime
    - Advanced Monitoring
    - Routine Maintenance
    - Backtrack: restore data at any point of time without using backups

---

# Aurora Security

- Similar to RDS because uses the same engines
- Encryption at rest using KMS
- Automated backups, snapshots and replicas are also encrypted
- Encryption in flight using SSL (same process as MySQL or Postgres)
- **Possibility to authenticate using IAM token (same method as RDS)**
- You are responsible for protecting the instance with security groups
- You can’t SSH

---

# Aurora Serverless

- Automated database instantiation and auto scaling based on actual usage
- Good for infrequent, intermittent or unpredictable workloads
- No capacity planning needed, no need to choose instance type (like vCPU, RAM)
- Pay per second, can be more cost-effective

![4%20Aurora/Untitled%204.png](4%20Aurora/Untitled%204.png)

- When client want to access Aurora database, there's gonna be an Amazon Aurora created by Aurora Serverless
- There's a proxy fleet, managed by Aurora, that our client will connect to
- Then proxy fleet will transfer it to our Amazon Aurora database.
- If we get more load, more Amazon Aurora databases will be created for us automatically
- If we get less load, then less databases will be going, all the way up to 0 Aurora databases

---

# Global Aurora

2 ways to have Global Aurora across multiple regions

- **Aurora Cross Region Read Replicas: (simple way)**
    - Useful for disaster recovery
    - Simple to put in place
- **Aurora Global Database (new way, recommended by documentation):**
    - 1 Primary Region (read / write)
    - Up to 5 secondary (read-only) regions, replication lag is less than 1 second
    - Up to 16 Read Replicas per secondary region
    - Helps for decreasing latency
    - Promoting another region (for disaster recovery) has an RTO (Recovery Time Object) of < 1 minute

For example: 

- we have primary region in us-east-1, application will do read / write
- we define secondary region in eu-west-1, we also define an Aurora Global Database which will perform some replication with up to 1 seconds lag.
- application in eu-west-1 can directly read from this database and perform read only workloads

![4%20Aurora/Untitled%205.png](4%20Aurora/Untitled%205.png)