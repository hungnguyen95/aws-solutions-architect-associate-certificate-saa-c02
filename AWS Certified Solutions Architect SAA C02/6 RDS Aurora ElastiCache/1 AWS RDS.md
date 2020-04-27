# 1. AWS RDS

- RDS stands for Relational Database Service
- It’s a managed DB service for DB use SQL as a query language
- It allows you to create databases in the cloud that are managed by AWS
    - Postgres
    - MySQL
    - MariaDB
    - Oracle
    - Microsoft SQL Server
    - Aurora (AWS Proprietary database)

---

# Advantage over using RDS versus deploying DB on EC2

- RDS is a managed service:
    - Automated provisioning, OS patching
    - Continuous backups and restore to specific timestamp (Point in Time Restore)!
    - Monitoring dashboards
    - Read replicas for improved read performance
    - Multi AZ setup for DR (Disaster Recovery)
    - Maintenance windows for upgrades
    - Scaling capability (vertical and horizontal)
    - Storage backed by EBS (gp2 or io1)
- BUT you can’t SSH into your RDS instances

---

# RDS Backup

- Backups are automatically enabled in RDS
- Automated backups:
    - Daily full backup of the database (during the maintenance window)
    - Transaction logs are backed-up by RDS every 5 minutes

    ⇒ ability to restore to any point in time (from oldest backup to 5 minutes ago)

    - 7 days retention (can be increased to 35 days)
- DB Snapshots:
    - Manually triggered by the user
    - Retention of backup for as long as you want