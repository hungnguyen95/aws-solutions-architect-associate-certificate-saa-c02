# Placement Groups

- Sometimes you want control over the EC2 Instance placement strategy

    → Want to use them when we want to have control over how our EC2 instances are going to be placed within the AWS infrastructure.

- That strategy can be defined using placement groups
- When you create a placement group, you specify one of the following strategies for the group:

    [1. Placement Group Cluster](Placement%20Groups/1%20Placement%20Group%20Cluster.md)

    *Cluster*—clusters instances into a low-latency group in a single Availability Zone

    [2. Placement Group Spread](Placement%20Groups/2%20Placement%20Group%20Spread.md)

    *Spread*—spreads instances across underlying hardware (max 7 instances per group per AZ) - critical applicaiton

    [3. Placement Group Partition](Placement%20Groups/3%20Placement%20Group%20Partition.md)

    *Partition*—spreads instances across many different partitions (which rely on different sets of racks) within an AZ. Scales to 100s of EC2 instances per group(Hadoop, Cassandra, Kafka)