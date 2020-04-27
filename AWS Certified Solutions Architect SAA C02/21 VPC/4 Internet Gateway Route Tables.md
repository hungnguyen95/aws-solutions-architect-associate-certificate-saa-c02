# 4. Internet Gateway & Route Tables

- Internet gateways helps our VPC instances connect with the internet
- It scales horizontally and is HA and redundant
- Must be created separately from VPC
- One VPC can only be attached to one IGW and vice versa
- Internet Gateway is also a NAT for the instances that have a public IPv4

- Internet Gateways on their own do not allow internet access…
- Route tables must also be edited!

---

# Adding IGW

![4%20Internet%20Gateway%20Route%20Tables/Untitled.png](4%20Internet%20Gateway%20Route%20Tables/Untitled.png)

- 1 Internet Gateway ↔ 1 VPC

---

# Editing Route Tables

![4%20Internet%20Gateway%20Route%20Tables/Untitled%201.png](4%20Internet%20Gateway%20Route%20Tables/Untitled%201.png)

- Edit Route Table
    - Talk to any local IP → Set Target in route table is `local`
    - Talk to other IP (not local) → Set Target in route table is `internet-gateway`

    ![4%20Internet%20Gateway%20Route%20Tables/Untitled%202.png](4%20Internet%20Gateway%20Route%20Tables/Untitled%202.png)

---