# 2. RDS Read Replica & Multi AZ

# RDS Read Replicas for read scalability

- Read replica ⇒ Help you to scale your read
- Up to 5 Read Replicas
- Within AZ, Cross AZ or Cross Region
- Replication is **ASYNC**, so reads are eventually consistent
- Replicas can be promoted to their own DB
- Applications must update the connection string to leverage read replicas

![2%20RDS%20Read%20Replica%20Multi%20AZ/Untitled.png](2%20RDS%20Read%20Replica%20Multi%20AZ/Untitled.png)

---

# RDS Read Replicas – Use Cases

- You have a production database that is taking on normal load
- You want to run a reporting application to run some analytics
- You want to run a reporting application to run some analytics
- The production application is unaffected
- Read replicas are used for SELECT(=read) only kind of statements(not INSERT, UPDATE, DELETE)

![2%20RDS%20Read%20Replica%20Multi%20AZ/Untitled%201.png](2%20RDS%20Read%20Replica%20Multi%20AZ/Untitled%201.png)

---

# RDS Read Replicas – Network Cost

- In AWS there’s a network cost when data goes from one AZ to another
- As we replicate the data from 1a to 1b, asynchronously. Because the data goes from one AZ to another AZ, then it's going to go across AZ → it's going to cost us a lot of money

![2%20RDS%20Read%20Replica%20Multi%20AZ/Untitled%202.png](2%20RDS%20Read%20Replica%20Multi%20AZ/Untitled%202.png)

- To reduce the cost, you can have your Read Replicas in the same AZ

![2%20RDS%20Read%20Replica%20Multi%20AZ/Untitled%203.png](2%20RDS%20Read%20Replica%20Multi%20AZ/Untitled%203.png)

---

# RDS Multi AZ (Disaster Recovery)

- **SYNC** replication
- One DNS name – automatic app failover to standby
- Increase **availability**
- Failover in case of loss of AZ, loss of network, instance or storage failure
- No manual intervention in apps
- Not used for scaling

⇒ Note: The Read Replicas can be setup as Multi AZ for Disaster Recovery (DR)

![2%20RDS%20Read%20Replica%20Multi%20AZ/Untitled%204.png](2%20RDS%20Read%20Replica%20Multi%20AZ/Untitled%204.png)