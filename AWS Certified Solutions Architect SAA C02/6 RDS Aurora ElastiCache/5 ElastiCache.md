# 5. ElastiCache

# Overview

- The same way RDS is to get managed Relational Databases...
- ElastiCache is to get managed Redis or Memcached
- Caches are in-memory databases with really high performance, low latency
- Helps reduce load off of databases for read intensive workloads
- Helps make your application stateless
- Write Scaling using sharding
- Read Scaling using Read Replicas
- MultiAZ with Failover Capability
- AWS takes care of OS maintenance / patching, optimizations, setup,configuration, monitoring, failure recovery and backups
- **Using ElastiCache involves heavy application code changes**

---

# DB Cache

- Applications queries ElastiCache, if not available, get from RDS and store in ElastiCache
- Helps relieve load in RDS
- Cache must have an invalidation strategy to make sure only the most current data is used in there.

![5%20ElastiCache/Untitled.png](5%20ElastiCache/Untitled.png)

---

# User Session Store

- User logs into any of the application
- The application writes the session data into ElastiCache
- The user hits another instance of our application
- The instance retrieves the data and the user is already logged in

⇒ Share some states, such as user session store into a common ground, such as all the applications can be stateless and retrieve, and write these sessions in real time

![5%20ElastiCache/Untitled%201.png](5%20ElastiCache/Untitled%201.png)

---

# Redis vs Memcached

**REDIS**

- **Multi AZ** with Auto-Failover
- **Read Replicas** to scale reads and have **high availability**
- Data Durability using AOF persistence
- **Backup and restore features**

    ![5%20ElastiCache/Untitled%202.png](5%20ElastiCache/Untitled%202.png)

**MEMCACHED**

- Multi-node for partitioning of data  (sharding)

    Using multiple nodes for partitioning data ⇒ sharding

- **Non persistent**

    If your memcached node goes down, then the data is lost

- **No backup and restore**
- Multi-threaded architecture

    A part of the cache is going to be on the first shard, another part of cache is going to be on the second shard.

    ![5%20ElastiCache/Untitled%203.png](5%20ElastiCache/Untitled%203.png)

⇒ Redis is going to be more like RDS

⇒ Memcached is going to be a pure cache, that's going to live in memory, but there's going to be no backup and restore, no persistence, multi-thread.

---

# Cache Security

- Support SSL in flight encryption
- **Do not support IAM authentication**
- IAM policies on ElastiCache are only used for AWS API-level security
- **Redis AUTH**
    - You can set a “password/token” when you create a Redis cluster
    - This is an extra level of security for your cache(on top of security groups)
- Memcached
    - Supports SASL-based authentication (advanced)

![5%20ElastiCache/Untitled%204.png](5%20ElastiCache/Untitled%204.png)

---

# ElastiCache for Solutions Architects

- Patterns for ElastiCache
    - **Lazy Loading**: all the read data is cached, data can become stale in cache
    - **Write Through**: Adds or update data in the cache when written to a DB (no stale data)
    - **Session Store**: store temporary session data in a cache (using TTL features)