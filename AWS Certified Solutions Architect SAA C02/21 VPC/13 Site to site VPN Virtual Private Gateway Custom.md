# 13. Site to site VPN, Virtual Private Gateway & Customer Gateway

- Virtual Private Gateway
    - VPN concentrator on the AWS side of the VPN connection
    - VGW is created and attached to the VPC from which you want to create the Site-to-Site VPN connection
- Customer Gateway:
    - Software application or physical device on customer side of the VPN connection
    - IP Address:
        - Use static, internet-routable IP address for your customer gateway device.
        - If behind a CGW behind NAT (with NAT-T), use the public IP address of the NAT

![13%20Site%20to%20site%20VPN%20Virtual%20Private%20Gateway%20Custom/Untitled.png](13%20Site%20to%20site%20VPN%20Virtual%20Private%20Gateway%20Custom/Untitled.png)