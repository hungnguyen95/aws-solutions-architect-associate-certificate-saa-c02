# 3. Placement Group Partition

![3%20Placement%20Group%20Partition/Untitled.png](3%20Placement%20Group%20Partition/Untitled.png)

- Within the AZ, we'll have different partitions
- Partitions are sets of racks
- On each partition you will have different EC2 instances, so in this image above we have 4 EC2 instances per partitions and here we can see that within a partition all these EC2 instances could fail together, but across 2 partitions there is no failure that's shared.
- Up to 7 partitions per AZ
- Up to 100s of EC2 instances
- The instances in a partition don't share racks with the instances in the other partitions
- A partition failure can affect many EC2 but won’t affect other partitions
- EC2 instances get access to the partition information as metadata
- Use cases: HDFS, HBase, Cassandra, Kafka