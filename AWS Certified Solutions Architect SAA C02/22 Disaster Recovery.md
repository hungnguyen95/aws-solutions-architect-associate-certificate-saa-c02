# 22. Disaster Recovery

- Any event that has a negative impact on a company’s business continuity or finances is a disaster
- Disaster recovery (DR) is about preparing for and recovering from a disaster
- What kind of disaster recovery?
    - On-premise => On-premise: traditional DR, and very expensive
    - On-premise => AWS Cloud: hybrid recovery
    - AWS Cloud Region A => AWS Cloud Region B
- Need to define two terms:
    - RPO: Recovery Point Objective
    - RTO: Recovery Time Objective

---

# RPO and RTO

![22%20Disaster%20Recovery/Untitled.png](22%20Disaster%20Recovery/Untitled.png)

- RPO: How often basically you run backups

    ⇒ RPO is how much of data loss are you willing to accept in case of a disaster happens

- RTO: When you recover from the disaster

    Between disaster and RTO is the amount of downtime

---

# Disaster Recovery Strategies

- Backup and Restore
- Pilot Light
- Warm Standby
- Hot Site / Multi Site Approach

![22%20Disaster%20Recovery/Untitled%201.png](22%20Disaster%20Recovery/Untitled%201.png)

High RTO ↔ Small downtime

---

## Backup and Restore (High RPO)

![22%20Disaster%20Recovery/Untitled%202.png](22%20Disaster%20Recovery/Untitled%202.png)

---

## Disaster Recovery – Pilot Light

- A small version of the app is always running in the cloud
- Useful for the critical core (pilot light)
- Very similar to Backup and Restore
- Faster than Backup and Restore as critical systems are already up

![22%20Disaster%20Recovery/Untitled%203.png](22%20Disaster%20Recovery/Untitled%203.png)

---

## Warm Standby

- Full system is up and running, but at minimum size
- Upon disaster, we can scale to production load

![22%20Disaster%20Recovery/Untitled%204.png](22%20Disaster%20Recovery/Untitled%204.png)

---

## Multi Site / Hot Site Approach

- Very low RTO (minutes or seconds) – very expensive
- Full Production Scale is running AWS and On Premise

![22%20Disaster%20Recovery/Untitled%205.png](22%20Disaster%20Recovery/Untitled%205.png)

---

# All AWS Multi Region

![22%20Disaster%20Recovery/Untitled%206.png](22%20Disaster%20Recovery/Untitled%206.png)

---

# Disaster Recovery Tips

- **Backup**
    - EBS Snapshots, RDS automated backups / Snapshots, etc
    - Regular pushes to S3 / S3 IA / Glacier, Lifecycle Policy, Cross Region Replication
    - From On-Premise: Snowball or Storage Gateway
- **High Availability**
    - Use Route53 to migrate DNS over from Region to Region
    - RDS Multi-AZ, ElastiCache Multi-AZ, EFS, S3
    - Site to Site VPN as a recovery from Direct Connect
- **Replication**
    - RDS Replication (Cross Region), AWS Aurora + Global Databases
    - Database replication from on-premise to RDS
    - Storage Gateway
- **Automation**
    - CloudFormation / Elastic Beanstalk to re-create a whole new environment
    - Recover / Reboot EC2 instances with CloudWatch if alarms fail
    - AWS Lambda functions for customized automations
- **Chaos**
    - Netflix has a “simian-army” randomly terminating EC2

---

# [SAA-C02] Other disaster recovery

[1. Database Migration Service (DMS)](22%20Disaster%20Recovery/1%20Database%20Migration%20Service%20DMS.md)

[2. On-Premise Strategies with AWS](22%20Disaster%20Recovery/2%20On%20Premise%20Strategies%20with%20AWS.md)

[3. DataSync](22%20Disaster%20Recovery/3%20DataSync.md)

[4. Transferring large amount of data into AWS](22%20Disaster%20Recovery/4%20Transferring%20large%20amount%20of%20data%20into%20AWS.md)