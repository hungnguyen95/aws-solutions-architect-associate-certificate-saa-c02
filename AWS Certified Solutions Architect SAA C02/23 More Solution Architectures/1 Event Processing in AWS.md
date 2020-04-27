# 1. Event Processing in AWS

# Lambda, SNS & SQS

![1%20Event%20Processing%20in%20AWS/Untitled.png](1%20Event%20Processing%20in%20AWS/Untitled.png)

---

# Fan Out Pattern: deliver to multiple SQS

![1%20Event%20Processing%20in%20AWS/Untitled%201.png](1%20Event%20Processing%20in%20AWS/Untitled%201.png)

---

# S3 Events

- S3:ObjectCreated
- S3:ObjectRemoved
- S3:ObjectRestore
- S3:Replication
- ...
- Object name filtering possible (*.jpg)
- Use case: generate thumbnails of images uploaded to S3
- **Amazon S3 event notifications typically deliver events in seconds but can sometimes take a minute or longer. On very rare occasions, events might be lost.**

![1%20Event%20Processing%20in%20AWS/Untitled%202.png](1%20Event%20Processing%20in%20AWS/Untitled%202.png)

---