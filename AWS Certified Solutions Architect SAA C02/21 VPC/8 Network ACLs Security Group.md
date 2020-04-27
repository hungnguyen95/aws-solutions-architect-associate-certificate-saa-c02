# 8. Network ACLs & Security Group

# Incoming Request

![8%20Network%20ACLs%20Security%20Group/Untitled.png](8%20Network%20ACLs%20Security%20Group/Untitled.png)

- NACL inbound rules:
    - If inbound rules passes, then it will get passed on security groups inbound rule.

- Security group inbound rules & outbound rules (**stateful**):
    - If SGs inbound rule passed, then EC2 instance receive the request on the web server and going to serve it

    → The outbound will be allowed no matter what, because Security Groups are **stateful**.

    → If an inbound request passes then the outbound request will pass as well, even if there is a rule deny any traffic out of EC2 (rule: deny all outbound request from EC2)

- NACL outbound rules (**stateless**):
    - NACL outbound is stateless → Outbound rule will get evaluated

⇒ NACL is stateless, both inbound and outbound rule are stateless

⇒ SG is stateful, means that if a request go in to EC2 instance then it will go out no matter what outbound rule deny traffic or not.

---

# Outgoing Request

![8%20Network%20ACLs%20Security%20Group/Untitled%201.png](8%20Network%20ACLs%20Security%20Group/Untitled%201.png)

- Same as ingoing request
- If EC2 is send a request outside instance, it go through NACL (stateless) and SG inbound rule (stateful)
- Ex: if we send request to `[google.com](http://google.com)` we always receive response even deny all traffic in inbound rule

---

# Network ACLs

- NACL are like a firewall which control traffic from and to subnet

    → Security group is Instance Level

    → NACL iss subnet level

- Default NACL allows everything outbound and everything inbound
- **One NACL per Subnet, new Subnets are assigned the Default NACL**
- Define NACL rules:
    - Rules have a number (1-32766) and higher precedence with a lower number
    - E.g. If you define #100 ALLOW <IP> and #200 DENY <IP> , IP will be allowed

        → Because 100 have higher priority than 200, then <IP> is allowed

    - Last rule is an asterisk (*) and denies a request in case of no rule match
    - AWS recommends adding rules by increment of 100
- Newly created NACL will deny everything
- NACL are a great way of blocking a specific IP at the subnet level

![8%20Network%20ACLs%20Security%20Group/Untitled%202.png](8%20Network%20ACLs%20Security%20Group/Untitled%202.png)

![8%20Network%20ACLs%20Security%20Group/Untitled%203.png](8%20Network%20ACLs%20Security%20Group/Untitled%203.png)