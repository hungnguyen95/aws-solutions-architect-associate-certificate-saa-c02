# 7. EBS RAID Options

- EBS is already redundant storage (replicated within an AZ)
- But what if you want to increase IOPS to say 100 000 IOPS?
- What if you want to mirror your EBS volumes?
- You would mount volumes in parallel in RAID settings!
- RAID is possible as long as your OS supports it
- Some RAID options are:
    - RAID 0
    - RAID 1
    - RAID 5 (not recommended for EBS – see documentation)
    - RAID 6 (not recommended for EBS – see documentation)
- We’ll explore RAID 0 and RAID 1

---

# RAID 0 (increase performance)

![7%20EBS%20RAID%20Options/Untitled.png](7%20EBS%20RAID%20Options/Untitled.png)

→ RAID 0 is a way to gain performance.

For e.g: we have EC2 instance and it has one logical volume. But that volume is a bit special because it is bakced by two or more EBS volumes

When you do the write, it's either going to EBS Volume 1 or it will be going to EBS Volume 2.

So when you write data, for example I'm writing block A, B, C, D → they get distributed between the two volumes

- Combining 2 or more volumes and getting the total disk space and I/O

    So if your EBS Volume 1 is 50 GBs and EBS Volume 2 is 50GBs, you get 100 GBs

- But one disk fails, all the data is failed
- Use cases would be:
    - An application that needs a lot of IOPS and doesn’t need fault-tolerance
    - A database that has replication already built-in
- Using this, we can have a very big disk with a lot of IOPS
- For example
    - two 500 GiB Amazon EBS io1 volumes with 4,000 provisioned IOPS each will create a…
    - 1000 GiB RAID 0 array with an available bandwidth of 8,000IOPS and 1,000 MB/s of throughput EC2 instance EBS Volume 1 EBS Volume 2

---

# RAID 1 (increase fault tolerance)

![7%20EBS%20RAID%20Options/Untitled%201.png](7%20EBS%20RAID%20Options/Untitled%201.png)

For e.g: We have an EC2 instance hand has one logical volume exposed to it. We have 2 EBS Volumes

→ We're going to write both volumes at the same time

So anytime we write a block A on volume 1, it will also go to Volume 2.

Same as B and C

- RAID 1 = Mirroring a volume to another
- If one disk fails, our logical volume is still working
- We have to send the data to two EBS volume at the same time (2x network)

- Use cases:
    - Application that need increase volume fault tolerance
    - Application where you need to service disks
- For example:
    - two 500 GiB Amazon EBS io1 volumes with 4,000provisioned IOPS each will create a…
    - 500 GiB RAID 1 array with an available bandwidth of 4,000 IOPS and 500 MB/s of throughput