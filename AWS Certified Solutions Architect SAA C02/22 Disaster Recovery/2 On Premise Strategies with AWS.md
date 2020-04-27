# 2. On-Premise Strategies with AWS

- Ability to download Amazon Linux 2 AMI as a VM (.iso format)
    - VMWare, KVM, VirtualBox (Oracle VM), Microsoft Hyper-V
- VM Import / Export
    - Migrate existing applications into EC2
    - Create a DR repository strategy for your on-premise VMs
    - Can export back the VMs from EC2 to on-premise
- AWS Application Discovery Service
    - Gather information about your on-premise servers to plan a migration
    - Server utilization and dependency mappings
    - Track with AWS Migration Hub
- AWS Database Migration Service (DMS)
    - replicate On-premise => AWS , AWS => AWS, AWS => On-premise
    - Works with various database technologies (Oracle, MySQL, DynamoDB, etc..)
- AWS Server Migration Service (SMS)
    - Incremental replication of on-premise live servers to AWS