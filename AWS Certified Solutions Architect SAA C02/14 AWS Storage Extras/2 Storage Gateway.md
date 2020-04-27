# 2. Storage Gateway

# Hybrid Cloud for Storage

- AWS is pushing for "hybrid cloud":
    - Part of your infrastructure is on the cloud
    - Part of your infrastructure is on-premise
- This can be due to
    - Long cloud migrations
    - Security requirements
    - Compliance requirements
    - IT strategy
- S3 is a proprietary storage technology (unlike EFS / NFS), so how doyou expose the S3 data on-premise?

⇒ AWS Storage Gateway

---

# AWS Storage Gateway

- Bridge between on-premise data and cloud data in S3
- Use cases: disaster recovery, backup & restore, tiered storage
- 3 types of Storage Gateway:
    - File Gateway
    - Volume Gateway
    - Tape Gateway
- Exam Tip: You need to know the differences between all 3!

![2%20Storage%20Gateway/Untitled.png](2%20Storage%20Gateway/Untitled.png)

---

# File Gateway

- Configured S3 buckets are accessible using the NFS and SMB protocol
- Supports S3 standard, S3 IA, S3 One Zone IA
- Bucket access using IAM roles for each File Gateway
- Most recently used data is cached in the file gateway
- Can be mounted on many servers

![2%20Storage%20Gateway/Untitled%201.png](2%20Storage%20Gateway/Untitled%201.png)

---

# Volume Gateway

- Block storage using iSCSI protocol backed by S3
- Backed by EBS snapshots which can help restore on-premise volumes
- **Cached volumes**: low latency access to most recent data (most frequently used data)
- **Stored volumes**: entire dataset is on premise, scheduled backups to S3

![2%20Storage%20Gateway/Untitled%202.png](2%20Storage%20Gateway/Untitled%202.png)

---

# Tape Gateway

- Some companies have backup processes using physical tapes (!)
- With Tape Gateway, companies use the same processes but in the cloud
- Virtual Tape Library (VTL) backed by Amazon S3 and Glacier
- Back up data using existing tape-based processes (and iSCSI interface)
- Works with leading backup software vendors

![2%20Storage%20Gateway/Untitled%203.png](2%20Storage%20Gateway/Untitled%203.png)

---

# AWS Storage Gateway Summary

- On premise data to the cloud => Storage Gateway
- File access / NFS => File Gateway (backed by S3)
- Volumes / Block Storage / iSCSI => Volume gateway (backed by S3 with EBS snapshots)
- VTL Tape solution / Backup with iSCSI = > Tape Gateway (backed by S3 and Glacier)