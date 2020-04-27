# 4. Transferring large amount of data into AWS

- Example: transfer 200 TB of data in the cloud. We have a 100 Mbps internet connection.
- **Over the internet / Site-to-Site VPN:**
    - Immediate to setup
    - Will take 200(TB)*1000(GB)*1000(MB)*8(Mb)/100 Mbps = 16,000,000s = 185d
- **Over direct connect 1Gbps:**
    - Long for the one-time setup (over a month)
    - Will take 200(TB)*1000(GB)*8(Gb)/1 Gbps = 1,600,000s = 18.5d
- **Over Snowball:**
    - Will take 2 to 3 snowballs in parallel
    - Takes about 1 week for the end-to-end transfer
    - Can be combined with DMS
- **For on-going replication / transfers:** Site-to-Site VPN or DX with DMS or DataSync