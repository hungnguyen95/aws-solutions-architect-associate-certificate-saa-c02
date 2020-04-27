# 2. EBS Volume Types Use Case

# GP2

- Recommended for most workloads, least expensive for an SSD, can use it as a system boot volume
- System boot volumes
- Virtual desktops
- Low-latency interactive apps
- Development and test environments

- Size: 1 GiB - 16TiB
- Small gp2 volumes can burst IOPS to 3000
- Max IOPS is 16,000
- 3 IOPS per GB, means at 5,334GB we are at the max IOPS

    The rule for GP2: 3 IOPS per GB. Max IOPS = 16,000 = when you have a GP2 volume of 5334 GBs. Any size after this increase will not increase the number of IOPS.

---

# IO1

- Critical business applications that require sustained IOPS performance, or more than 16,000 IOPS per volume (gp2 limit)
- Large database workloads, such as:
- MongoDB, Cassandra, Microsoft SQL Server, MySQL, PostgreSQL, Oracle
- Size: 4 GiB - 16TiB
- IOPS is provisioned (PIOPS) – MIN 100 - MAX 64,000 (Nitro instances) else MAX 32,000 (other instances)

    64000 - only for this very specific type of instance

- The maximum ratio of provisioned IOPS to requested volume size (in GiB) is 50:1

---

# ST1

- Streaming workloads requiring consistent, fast throughput at a low price
- Big data, Data warehouses, Log processing
- Apache Kafka
- Cannot be a boot volume. Because it has a very specific kind of workloads.
- Size: 500 GiB - 16TiB
- Max IOPS is 500
- Max throughput of 500 MiB/s – can burst

---

# SC1

- Throughput-oriented storage for large volumes of data that is infrequently accessed
- Scenarios where the lowest storage cost is important
- Cannot be a boot volume.
- Size: 500 GiB - 16TiB
- Max IOPS is 250
- Max throughput of 250MiB/s – can burst

---

# Summary

- **gp2: General Purpose Volumes (cheap)**
    - 3 IOPS / GiB, minimum 100 IOPS, burst to 3000 IOPS, max 16000 IOPS
    - 1 GiB – 16TiB , +1 GB = +3000 IOPS

- **io1: Provisioned IOPS (expensive)**
    - Min 100 IOPS, Max 64000 IOPS (Nitro) or 32000 (other)
    - 4 GiB - 16TiB. Size of volume and IOPS are independent

- **st1: Throughput Optimized HDD**
    - 500 GiB – 16TiB , 500 MiB /s throughput

- **sc1: Cold HDD, Infrequently accessed data**
    - 250 GiB – 16TiB , 250 MiB /s throughput