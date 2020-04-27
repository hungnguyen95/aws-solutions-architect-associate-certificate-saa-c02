# Private vs Public IP (IPv4)

![Private%20vs%20Public%20IP%20IPv4/Untitled.png](Private%20vs%20Public%20IP%20IPv4/Untitled.png)

- Public IP
    - Public IP means the machine can be identified on the internet (WWW)
    - Must be unique across the whole web (not two machines can have same public IP).
    - Can be geo-located easily

- Private IP
    - Private IP means the machine can only be identified on a private network only
    - The IP must be unique across the private network
    - BUT two different private networks (two companies) can have the same IPs
    - Machines connect to WWW using an internet gateway (a proxy)
    - Only a specified range of IPs can be used as private IP

---

# Private and Public IP in EC2

- By default, your EC2 machines comes with:
    - A private IP for the internal AWS Network
    - A public IP, for the WWW

- When we are doing SSH into our EC2 machines:
    - We can’t use a private IP, because we are not in the same network
    - We can only use the public IP

- If your machine is stopped and then started, the public IP can change