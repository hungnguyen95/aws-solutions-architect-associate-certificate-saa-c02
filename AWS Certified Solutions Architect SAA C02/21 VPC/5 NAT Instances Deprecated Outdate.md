# 5. NAT Instances (Deprecated/Outdate)

- Allows instances in the private subnets to connect to the internet
- Must be launched in a public subnet
- Must disable EC2 flag: Source / Destination Check
- Must have Elastic IP attached to it
- Route table must be configured to route traffic from private subnets to NAT Instance

---

![5%20NAT%20Instances%20Deprecated%20Outdate/Untitled.png](5%20NAT%20Instances%20Deprecated%20Outdate/Untitled.png)

## NAT Instances – Comments

- Amazon Linux AMI pre-configured are available
- Not highly available / resilient setup out of the box

    ⇒ Would need to create ASG in multi AZ + resilient user-data script

- Internet traffic bandwidth depends on EC2 instance performance
- Must manage security groups & rules:
    - Inbound:
        - Allow HTTP / HTTPS Traffic coming from Private Subnets
        - Allow SSH from your home network (access is provided through Internet Gateway)
    - Outbound:
        - Allow HTTP / HTTPS traffic to the internet