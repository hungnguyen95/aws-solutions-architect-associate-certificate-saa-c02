# 13. AWS Global Accelerator

# Global users for our application

- You have deployed an application and have global user who want to access it directly.
- They go over the public internet, which can add a lot of latency due to many hops
- We wish to go as fast as possible through AWS network to minimize latency

![13%20AWS%20Global%20Accelerator/Untitled.png](13%20AWS%20Global%20Accelerator/Untitled.png)

---

# Unicast IP vs Anycast IP

- **Unicast IP**: one server holds one IP address

    Each server have individual IP address. When user request to specific IP address, it will route to the server associated with that IP.

![13%20AWS%20Global%20Accelerator/Untitled%201.png](13%20AWS%20Global%20Accelerator/Untitled%201.png)

- **Anycast IP**: all servers hold the same IP address and the client is routed to the nearest one

![13%20AWS%20Global%20Accelerator/Untitled%202.png](13%20AWS%20Global%20Accelerator/Untitled%202.png)

---

# AWS Global Accelerator

- Leverage the AWS internal network to route to your application
- **2 Anycast IP** are created for your application
- The Anycast IP send traffic directly to Edge Locations
- The Edge locations send the traffic to your application

![13%20AWS%20Global%20Accelerator/Untitled%203.png](13%20AWS%20Global%20Accelerator/Untitled%203.png)

- Works with **Elastic IP, EC2 instances, ALB, NLB, public or private**
- Consistent Performance
    - Intelligent routing to lowest latency and fast regional failover
    - No issue with client cache (because the IP doesn’t change)
    - Internal AWS network
- Health Checks
    - Global Accelerator performs a health check of your applications
    - Helps make your application global (failover less than 1 minute for unhealthy)
    - Great for disaster recovery (thanks to the health checks)
- Security
    - only 2 external IP need to be whitelisted
    - DDoS protection thanks to AWS Shield

---

# AWS Global Accelerator vs CloudFront

- They both use the AWS global network and its edge locations around the world
- Both services integrate with AWS Shield for DDoS protection
- CloudFront
    - Improves performance for both cacheable content (such as images and videos)
    - Dynamic content (such as API acceleration and dynamic site delivery)
    - Content is served at the edge
- Global Accelerator
    - Improves performance for a wide range of applications over TCP or UDP
    - Proxying packets at the edge to applications running in one or more AWS Regions
    - Good fit for non-HTTP use cases, such as gaming (UDP), IoT (MQTT), or Voice over IP
    - Good for HTTP use cases that require static IP addresses
    - Good for HTTP use cases that required deterministic, fast regional failover

![13%20AWS%20Global%20Accelerator/Untitled%204.png](13%20AWS%20Global%20Accelerator/Untitled%204.png)