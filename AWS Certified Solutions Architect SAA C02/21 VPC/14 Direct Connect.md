# 14. Direct Connect

- Provides a dedicated **private** connection from a remote network to your VPC
- Dedicated connection must be setup between your DC and AWS Direct Connect locations
- You need to setup a Virtual Private Gateway on your VPC
- Access public resources (S3) and private (EC2) on same connection
- Use Cases:
    - Increase bandwidth throughput - working with large data sets – lower cost
    - More consistent network experience - applications using real-time data feeds
    - Hybrid Environments (on prem + cloud)
- Supports both IPv4 and IPv6

![14%20Direct%20Connect/Untitled.png](14%20Direct%20Connect/Untitled.png)

---

# Direct Connect Gateway

- If you want to setup a Direct Connect to one or more VPC in many different regions (same account), you must use a Direct Connect Gateway

![14%20Direct%20Connect/Untitled%201.png](14%20Direct%20Connect/Untitled%201.png)

VPC (Virtual Private Gateway) ↔ Direct connect gateway ↔ Direct connect connection ↔ Customer gateway (customer network)

---

# Direct Connect – Connection Types

- **Dedicated Connections**: 1Gbps and 10 Gbps capacity
    - Physical ethernet port dedicated to a customer
    - Request made to AWS first, then completed by AWS Direct Connect Partners

- **Hosted Connections**: 50Mbps, 500 Mbps, to 10 Gbps
    - Connection requests are made via AWS Direct Connect Partners
    - Capacity can be **added or removed on demand**
    - 1, 2, 5, 10 Gbps available at select AWS Direct Connect Partners

- **Lead times are often longer than 1 month to establish a new connection**

---

# Direct Connect – Encryption

- Data in transit is not encrypted but is private
- AWS Direct Connect + VPN provides an IPsec-encrypted private connection
- Good for an extra level of security, but slightly more complex to put in place

![14%20Direct%20Connect/Untitled%202.png](14%20Direct%20Connect/Untitled%202.png)