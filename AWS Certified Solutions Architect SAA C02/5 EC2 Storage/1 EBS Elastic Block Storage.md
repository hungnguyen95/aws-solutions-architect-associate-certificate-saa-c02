# 1. EBS (Elastic Block Storage)

# What is an EBS volume?

- An EC2 machine loses its root volume (main drive) when it is manually terminated.
- Unexpected terminations might happen from time to time (AWS would email you)
- Sometimes, you need a way to store your instance data somewhere

    You don't want your data to be on your root volume, you want it to be on an attached volume.

    → That attached volume is going to be an EBS Volume.

- An EBS (Elastic Block Store) Volume is a network drive you can attach to your instances while they run
- It allows your instances to persist data

---

# EBS Volume

- It’s a network drive (i.e. not a physical drive)
    - It uses the network to communicate the instance, which means there might be a bit of latency
    - It can be detached from an EC2 instance and attached to another one quickly
- It’s locked to an Availability Zone (AZ)
    - An EBS Volume in us-east-1a cannot be attached to us-east-1b
    - To move a volume across, you first need to snapshot it
- Have a provisioned capacity (size in GBs, and IOPS)
    - Have a provisioned capacity (size in GBs, and IOPS)

        So if you provision 1TB of a disk, but you only use 1GB, you're still going to get billed for 1TB.

    - You can increase the capacity of the drive over time

---

# EBS Volume Example

![1%20EBS%20Elastic%20Block%20Storage/Untitled.png](1%20EBS%20Elastic%20Block%20Storage/Untitled.png)

- In US-EAST-1A: We have 3 EC2 Instances
    - The first: 10GB
    - The second: 100GB and 50GB
    - The third: nothing
- In US-EAST-1B: We have 2 EC2 Instances
    - The first: nothing
    - The second: 50GB

→ EBS Volume are scoped to specific AZ. I cannot attach my volumes of us-east-1a to an instance in us-east-1b

---

# EBS Volume Types

- EBS Volumes come in 4 types
    - GP2 (SSD): General purpose SSD volume that balances price and performance for a wide variety of workloads
    - IO1 (SSD): Highest-performance SSD volume for mission-critical low-latency or high throughput workloads

        → Usually running your critical database

    - ST1 (HDD): Low cost HDD volume designed for frequently accessed, throughput intensive workloads

        → It's going to be more around looking more throughput and running big data workloads.

    - SC1 (HDD): Lowest cost HDD volume designed for less frequently accessed workloads

        → Also for big data but for less frequently accessed workloads usually.

- EBS Volumes are characterized in Size | Throughput | IOPS (I/O Ops Per Sec)
- **Only GP2 and IO1 can be used as boot volumes**