# 12. AWS CloudFront

- Content Delivery Network (CDN)
- Improves read performance, content is cached at the edge
- 216 Point of Presence globally (edge locations)
- DDoS protection, integration with Shield, AWS Web Application Firewall
- Can expose external HTTPS and can talk to internal HTTPS backends

![12%20AWS%20CloudFront/Untitled.png](12%20AWS%20CloudFront/Untitled.png)

---

# CloudFront – Origins

Origins are what CloudFront can source data from

- **S3 bucket**
    - For distributing files and caching them at the edge
    - Enhanced security with CloudFront **Origin Access Identity (OAI)**
    - CloudFront can be used as an ingress (to upload files to S3)

    ⇒ Can upload file via CloudFront

- **S3 website**
    - Must first enabled the bucket as a static S3 website
- **Custom Origin (HTTP) – Must be publicly accessible**
    - Application Load Balancer
    - EC2 instance
    - Any HTTP backend you want

---

# S3 as an Origin

![12%20AWS%20CloudFront/Untitled%201.png](12%20AWS%20CloudFront/Untitled%201.png)

- Edge location is going to fetch data from S3 bucket over the private AWS network
- To access S3 bucket: use an OAI.

    It's IAM role for CloudFront origin, using that role, bucket policy will make edge location accessible

---

# ALB or EC2 as an origin

![12%20AWS%20CloudFront/Untitled%202.png](12%20AWS%20CloudFront/Untitled%202.png)

---

# CloudFront Geo Restriction

- You can restrict who can access your distribution
    - **Whitelist**: Allow your users to access your content only if they're in one of the countries on a list of approved countries.
    - **Blacklist**: Prevent your users from accessing your content if they're in one of the countries on a blacklist of banned countries.
- The “country” is determined using a 3rd party Geo-IP database
- Use case: Copyright Laws to control access to content

---

# CloudFront vs S3 Cross Region Replication

- CloudFront:
    - Global Edge network
    - Files are cached for a TTL (maybe a day)
    - **Great for static content that must be available everywhere**
- S3 Cross Region Replication:
    - Must be setup for each region you want replication to happen
    - Files are updated in near real-time
    - **Great for dynamic content that needs to be available at low-latency in few regions**

---

# CloudFront Signed URL / Signed Cookies

- You want to distribute paid shared content to premium users over the world
- We can use CloudFront Signed URL / Cookie. We attach a policy with:
    - Includes URL expiration
    - Includes IP ranges to access the data from
    - Trusted signers (which AWS accounts can create signed URLs)
- How long should the URL be valid for?
    - Shared content (movie, music): make it short (a few minutes)
    - Private content (private to the user): you can make it last for years
- Signed URL = access to individual files (one signed URL per file)
- Signed Cookies = access to multiple files (one signed cookie for many files)

![12%20AWS%20CloudFront/Untitled%203.png](12%20AWS%20CloudFront/Untitled%203.png)

## CloudFront Signed URL vs S3 Pre-Signed URL

- CloudFront Signed URL:
    - Allow access to a path, no matter the origin
    - Account wide key-pair, only the root can manage it
    - Can filter by IP, path, date, expiration
    - Can leverage caching features

![12%20AWS%20CloudFront/Untitled%204.png](12%20AWS%20CloudFront/Untitled%204.png)

- **S3 Pre-Signed URL:**
    - Issue a request as the person who pre-signed the URL
    - Uses the IAM key of the signing IAM principal
    - Limited lifetime

![12%20AWS%20CloudFront/Untitled%205.png](12%20AWS%20CloudFront/Untitled%205.png)