# 1. Snowball

- Physical data transport solution that helps moving TBs or PBs of data in or out of AWS
- Alternative to moving data over the network (and paying network fees)
- Secure, tamper resistant, uses KMS 256 bit encryption
- Tracking using SNS and text messages. E-ink shipping label
- Pay per data transfer job
- Use cases: large data cloud migrations, DC decommission, disaster recovery
- If it takes more than a week to transfer over the network, use Snowball devices!

![1%20Snowball/Untitled.png](1%20Snowball/Untitled.png)

---

# Snowball Process

1. Request snowball devices from the AWS console for delivery
2. Install the snowball client on your servers
3. Connect the snowball to your servers and copy files using the client
4. Ship back the device when you’re done (goes to the right AWS facility)
5. Data will be loaded into an S3 bucket
6. Snowball is completely wiped
7. Tracking is done using SNS, text messages and the AWS console

---

# Diagrams

- Direct upload to S3:

![1%20Snowball/Untitled%201.png](1%20Snowball/Untitled%201.png)

- With snowball

![1%20Snowball/Untitled%202.png](1%20Snowball/Untitled%202.png)

---

# Snowball Edge

- Snowball Edges add computational capability to the device
- 100 TB capacity with either:
    - Storage optimized – 24 vCPU
    - Compute optimized – 52 vCPU & optional GPU
- Supports a custom EC2 AMI so you can perform processing on the go
- Supports custom Lambda functions
- Very useful to pre-process the data while moving
- Use case: data migration, image collation, IoT capture, machine learning

---

# AWS Snowmobile

![1%20Snowball/Untitled%203.png](1%20Snowball/Untitled%203.png)

- Transfer exabytes of data (1 EB = 1,000 PB = 1,000,000 TBs)
- Each Snowmobile has 100 PB of capacity (use multiple in parallel)
- Better than Snowball if you transfer more than 10 PB