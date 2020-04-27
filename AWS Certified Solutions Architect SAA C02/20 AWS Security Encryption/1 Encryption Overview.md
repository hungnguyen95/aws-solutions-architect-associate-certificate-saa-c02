# 1. Encryption Overview

# Encryption in flight (SSL)

- Data is encrypted before sending and decrypted after receiving
- SSL certificates help with encryption (HTTPS)
- Encryption in flight ensures no MITM (man in the middle attack) can happen

![1%20Encryption%20Overview/Untitled.png](1%20Encryption%20Overview/Untitled.png)

---

# Server side encryption at rest

- Data is encrypted after being received by the server
- Data is decrypted before being sent
- It is stored in an encrypted form thanks to a key (usually a data key)
- The encryption / decryption keys must be managed somewhere and the server must have access to it

![1%20Encryption%20Overview/Untitled%201.png](1%20Encryption%20Overview/Untitled%201.png)

---

# Client side encryption

- Data is encrypted by the client and never decrypted by the server
- Data will be decrypted by a receiving client
- The server should not be able to decrypt the data
- Could leverage **Envelope Encryption**

![1%20Encryption%20Overview/Untitled%202.png](1%20Encryption%20Overview/Untitled%202.png)