# 15. Egress only Internet Gateway

- Egress only Internet Gateway is for IPv6 only
- Similar function as a NAT, but a NAT is for IPv4
- Good to know: IPv6 are all public addresses
- Therefore all our instances with IPv6 are publicly accessibly
- Egress Only Internet Gateway gives our IPv6 instances access to the internet, but they won’t be directly reachable by the internet
- After creating an Egress Only Internet Gateway, edit the route tables