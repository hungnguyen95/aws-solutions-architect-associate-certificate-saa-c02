# 6. EBS vs Instance Store

- Some instance do not come with Root EBS volumes
- Instead, they come with “Instance Store” (= ephemeral storage)
- Instance store is physically attached to the machine (EBS is a network drive)

    That's the big racks inside Amazon's data centers. Some of these machines, some of these EC2 instances we get, they will have a physically attached disk, and that will be an instance store.

- Pros:
    - Better I/O performance (EBS gp2 has an max IOPS of 16000, io1 of 64000)
    - Good for buffer / cache / scratch data / temporary content
    - Data survives reboots
- Cons:
    - On stop or termination, the instance store is lost
    - You can’t resize the instance store
    - Backups must be operated by the user

⇒ **If an instance store reboots (intentionally or unintentionally), data in the instance store persists. On stop or termination, the instance store is lost**

---

# Local EC2 Instance Store

- **Physical disk attached to the physical server where your EC2 is**
- Very High IOPS (because physical)
- Disks up to 7.5TiB (can changeover time), stripped to reach 30TiB (can change over time…)
- Block Storage (just like EBS)
- Cannot be increased in size
- Risk of data loss if hardware fails

![6%20EBS%20vs%20Instance%20Store/Untitled.png](6%20EBS%20vs%20Instance%20Store/Untitled.png)