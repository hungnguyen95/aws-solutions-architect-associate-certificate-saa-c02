# 1. CIDR, Public, Private IPs

# Understanding CIDR - IPv4 (Classless Inter-Domain Routing)

- CIDR are used for Security Groups rules, or AWS networking in general

![1%20CIDR%20Public%20Private%20IPs/Untitled.png](1%20CIDR%20Public%20Private%20IPs/Untitled.png)

- They help to define an IP address range
    - We’ve seen WW.XX.YY.ZZ/**32** == one IP
    - We’ve seen 0.0.0.0/**0** == all IPs
    - But we can define for ex: 192.168.0.0/**26**: 192.168.0.0 – 192.168.0.63 (64 IP)

---

# Understanding CIDR

- A CIDR has two components:
    - The base IP (XX.XX.XX.XX)
    - The Subnet Mask (/26)
- The base IP represents an IP contained in the range
- The subnet masks defines how many bits can change in the IP
- The subnet mask can take two forms. Examples:
    - `255.255.255.0` ← less common
    - `/24`                  ← more common

---

# Understanding CIDRs Subnet Masks

- The subnet masks basically allows part of the underlying IP to get additional next values from the base IP
- /32 allows for 1 IP = 2^0
- /31 allows for 2 IP = 2^1
- /24 allows for 256 IP = 2^8
- /16 allows for 65,536 IP = 2^16
- /0 allows for all IPs = 2^32

⇒ `/x` allows for all IPs = `2^(32 - x)`

![1%20CIDR%20Public%20Private%20IPs/Untitled%201.png](1%20CIDR%20Public%20Private%20IPs/Untitled%201.png)

- 192.168.0.0/24 = … ?
    - 192.168.0.0 – 192.168.0.255 (256 IP)
- 192.168.0.0/16 = … ?
    - 192.168.0.0 – 192.168.255.255 (65,536 IP)

---

# Private vs Public IP (IPv4) Allowed ranges

- The Internet Assigned Numbers Authority (IANA) established certain blocks of IPV4 addresses for the use of private (LAN) and public(Internet) addresses.

- Private IP can only allow certain values
    - 10.0.0.0 – 10.255.255.255 (10.0.0.0/8) <= in big networks
    - 172.16.0.0 – 172.31.255.255 (172.16.0.0/12) <= default AWS one
    - 192.168.0.0 – 192.168.255.255 (192.168.0.0/16) <= example: home networks

- All the rest of the IP on the internet are public IP