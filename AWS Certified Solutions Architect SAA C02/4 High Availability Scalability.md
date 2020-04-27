# 4. High Availability & Scalability

- Scalability means that an application / system can handle greater loads by adapting.
- There are two kinds of scalability:
    - Vertical Scalability
    - Horizontal Scalability (= elasticity)
- **Scalability is linked but different to High Availability**

[1. Vertical Scalability](4%20High%20Availability%20Scalability/1%20Vertical%20Scalability.md)

[2. Horizontal Scalability](4%20High%20Availability%20Scalability/2%20Horizontal%20Scalability.md)

[3. High Availability](4%20High%20Availability%20Scalability/3%20High%20Availability.md)

---

# High Availability & Scalability in EC2

- Vertical Scaling: Increase instance size (= scale up / down)
    - From: t2.nano - 0.5G of RAM, 1 vCPU
    - To: u-12tb1.metal – 12.3 TB of RAM, 448 vCPUs

- Horizontal Scaling: Increase number of instances (= scale out / in)
    - Auto Scaling Group
    - Load Balancer

- High Availability: Run instances for the same application across multi AZ
    - Auto Scaling Group multi AZ
    - Load Balancer multi AZ

---

# ELB (Elastic Load Balancing)

[4. ELB (Elastic Load Balancing)](4%20High%20Availability%20Scalability/4%20ELB%20Elastic%20Load%20Balancing.md)

[5. Auto Scaling Group](4%20High%20Availability%20Scalability/5%20Auto%20Scaling%20Group.md)