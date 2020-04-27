# 11. Flow Logs + Athena

- Capture information about IP traffic going into your interfaces:
    - VPC Flow Logs
    - Subnet Flow Logs
    - Elastic Network Interface Flow Logs
- Helps to monitor & troubleshoot connectivity issues
- Flow logs data can go to S3 / CloudWatch Logs
- Captures network information from AWS managed interfaces too: ELB, RDS, ElastiCache, Redshift, WorkSpaces

![11%20Flow%20Logs%20Athena/Untitled.png](11%20Flow%20Logs%20Athena/Untitled.png)

---

# Flow log syntax

- `<version> <account-id> <interface-id> <srcaddr> <dstaddr> <srcport> <dstport> <protocol> <packets> <bytes> <start> <end> <action> <logstatus>`
- `Srcaddr`, `dstaddr` help identify problematic IP
- `Srcport`, `dstport` help identity problematic ports
- `Action` : success or failure of the request due to Security Group / NACL
- Can be used for analytics on usage patterns, or malicious behavior
- **Query VPC flow logs using Athena on S3 or CloudWatch Logs Insights**

---

# How to troubleshoot SG vs NACL issue?

- **For incoming requests**
    - Inbound REJECT: NACL or SG
    - Inbound ACCEPT, outbound REJECT: NACL

    ![11%20Flow%20Logs%20Athena/Untitled%201.png](11%20Flow%20Logs%20Athena/Untitled%201.png)

- **For outgoing requests**
    - Outbound REJECT: NACL or SG
    - Outbound ACCEPT, inbound REJECT: NACL

    ![11%20Flow%20Logs%20Athena/Untitled%202.png](11%20Flow%20Logs%20Athena/Untitled%202.png)