# 3. EBS Snapshot

- Incremental – only backup changed blocks
- EBS backups use IO and you shouldn’t run them while your application is handling a lot of traffic
- Snapshots will be stored in S3 (but you won’t directly see them)
- Not necessary to detach volume to do snapshot, but recommended
- Max 100,000 snapshots / 1 account
- Can copy snapshots across AZ or Region
- Can make Image (AMI) from Snapshot
- **EBS volumes restored by snapshots need to be pre-warmed (using fio or dd command to read the entire volume)**
- **Snapshots can be automated using Amazon Data Lifecycle Manager**