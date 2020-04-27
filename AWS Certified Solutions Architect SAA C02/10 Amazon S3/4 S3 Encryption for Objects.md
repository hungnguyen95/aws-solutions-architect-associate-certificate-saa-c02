# 4. S3 Encryption for Objects

- There are 4 methods of encrypting objects in S3
    - **SSE-S3**: encrypts S3 objects using keys handled & managed by AWS
    - **SSE-KMS**: leverage AWS Key Management Service to manage encryption keys
    - **SSE-C**: when you want to manage your own encryption keys
    - Client Side Encryption

---

# SSE-S3

- SSE-S3: encryption using keys handled & managed by AWS S3
- Object is encrypted server side
- AES-256 encryption type
- Must set header: `"x-amz-server-side-encryption": "AES256"`

![4%20S3%20Encryption%20for%20Objects/Untitled.png](4%20S3%20Encryption%20for%20Objects/Untitled.png)

---

# SSE-KMS

- SSE-KMS: encryption using keys handled & managed by KMS
- KMS Advantages: user control + audit trail
- Object is encrypted server side
- Must set header: `"x-amz-server-side-encryption": "aws:kms"`

![4%20S3%20Encryption%20for%20Objects/Untitled%201.png](4%20S3%20Encryption%20for%20Objects/Untitled%201.png)

⇒ The difference between SSE-S3 and SSE-KMS is that this time the key that is used is a KMS Customer Master Key that you can manage over time.

---

# SSE-C

- SSE-C: server-side encryption using data keys fully managed by the customer outside of AWS
- Amazon S3 does not store the encryption key you provide
- **HTTPS must be used**
- Encryption key must provided in HTTP headers, for every HTTP request made

![4%20S3%20Encryption%20for%20Objects/Untitled%202.png](4%20S3%20Encryption%20for%20Objects/Untitled%202.png)

⇒ User provided Object and a Key, must be sent through **HTTPS** only. Amazon just does the encryption, but throws away the key right away after encryption.

---

# Client Side Encryption

- Should use Client library such as the Amazon S3 Encryption Client

    ⇒ Easier if use client library encryption

- Clients must encrypt data themselves before sending to S3
- Clients must decrypt data themselves when retrieving from S3
- Customer fully manages the keys and encryption cycle

![4%20S3%20Encryption%20for%20Objects/Untitled%203.png](4%20S3%20Encryption%20for%20Objects/Untitled%203.png)

---

# Encryption in transit (SSL)

- AWS S3 exposes:
    - HTTP endpoint: non encrypted
    - HTTPS endpoint: encryption in flight

- You’re free to use the endpoint you want, but HTTPS is recommended
- HTTPS is mandatory for SSE-C
- Encryption in flight is also called SSL / TLS