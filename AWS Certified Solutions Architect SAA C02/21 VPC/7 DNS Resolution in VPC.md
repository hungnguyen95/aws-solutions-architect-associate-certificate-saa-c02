# 7. DNS Resolution in VPC

- **enableDnsSupport: (= DNS Resolution setting)**
    - Default True
    - Helps decide if DNS resolution is supported for the VPC
    - If True, queries the AWS DNS server at 169.254.169.253
- **enableDnsHostname: (= DNS Hostname setting)**
    - False by default for newly created VPC, True by default for Default VPC
    - Won’t do anything unless enableDnsSupport=true
    - If True, Assign public hostname to EC2 instance if it has a public
- **If you use custom DNS domain names in a private zone in Route 53, you must set both these attributes to true**