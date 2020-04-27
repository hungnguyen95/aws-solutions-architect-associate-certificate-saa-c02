# 19. Summary

- **CIDR**: IP Range
- **VPC**: Virtual Private Cloud => we define a list of IPv4 & IPv6 CIDR
- **Subnets**: Tied to an AZ, we define a CIDR
- **Internet Gateway**: at the VPC level, provide IPv4 & IPv6 Internet Access
- **Route Tables**: must be edited to add routes from subnets to the IGW, VPC Peering

Connections, VPC Endpoints, etc…

- **NAT Instances**: gives internet access to instances in private subnets. Old, must be setup in a

public subnet, disable Source / Destination check flag

- **NAT Gateway**: managed by AWS, provides scalable internet access to private instances, IPv4

only

- **Private DNS + Route 53**: enable DNS Resolution + DNS hostnames (VPC)
- **NACL**: Stateless, subnet rules for inbound and outbound, don’t forget ephemeral ports
- **Security Groups**: Stateful, operate at the EC2 instance level
- **VPC Peering**: Connect two VPC with non overlapping CIDR, non transitive
- **VPC Endpoints**: Provide private access to AWS Services (S3, DynamoDB, CloudFormation, SSM) within VPC
- **VPC Flow Logs**: Can be setup at the VPC / Subnet / ENI Level, for ACCEPT and REJECT

traffic, helps identifying attacks, analyze using Athena or CloudWatch Log Insights

- **Bastion Host**: Public instance to SSH into, that has SSH connectivity to instances in private

subnets

- **Site to Site VPN:** setup a Customer Gateway on DC, a Virtual Private Gateway on VPC, and

site-to-site VPN over public internet

- **Direct Connect**: setup a Virtual Private Gateway on VPC, and establish a direct private

connection to an AWS Direct Connect Location

- **Direct Connect Gateway**: setup a Direct Connect to many VPC in different regions
- **Internet Gateway Egress**: like a NAT Gateway, but for IPv6
- **Private Link / VPC Endpoint Services:**
    - connect services privately from your service VPC to customers VPC
    - Doesn’t need VPC peering, public internet, NAT gateway, route tables
    - Must be used with Network Load Balancer & ENI
- **ClassicLink**: connect EC2-Classic instances privately to your VPC
- **VPN CloudHub**: hub-and-spoke VPN model to connect your sites