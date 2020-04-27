# 5. Route53 as a Registrar

- A domain name registrar is an organization that manages the reservation of Internet domain names
- Famous names:
    - GoDaddy
    - Google Domains
    - Etc…
- And also… Route53 (e.g. AWS)!
- **Domain Registrar != DNS**

---

# 3rd Party Registrar with AWS Route 53

- **If you buy your domain on 3rd party website, you can still use Route53**
1. Create a Hosted Zone in Route 53
2. Update NS Records on 3rd party website to use Route 53 **name servers**

- **Domain Registrar != DNS**
- (But each domain registrar usually comes with some DNS features)