# 8. EFS (Elastic File System)

- Managed NFS (network file system) that can be mounted on many EC2
- EFS works with EC2 instances in multi-AZ

    → Within the same region but as many AZs on as you want

    → Opposed to EBS, EBS can only mount on EC2 instances which are same AZs

- Highly available, scalable, expensive (3x gp2), pay per use

![8%20EFS%20Elastic%20File%20System/Untitled.png](8%20EFS%20Elastic%20File%20System/Untitled.png)

Here is your Security Group and your EFS, so you have to attach a security group to your EFS network drive.

So you can attach an EC2 instance from us-east-1a, 1b or 1-c

→ They can all talk to the same EFS at the same time, which kind of cool.

- Use cases: content management, web serving, data sharing, Wordpress
- Uses NFSv4.1 protocol
- Uses security group to control access to EFS
- Compatible with Linux based AMI (not Windows)
- Performance mode:
    - General purpose (default)
    - Max I/O – used when thousands of EC2 are using the EFS
- EFS file sync to sync from on-premise file system to EFS

    You can basically sync your local network file system to the EFS

- Backup EFS-to-EFS (incremental – can choose frequency)
- Encryption at rest using KMS