# 3. Directory Services

- Found on any Windows Server with AD Domain Services
- Database of **objects**: User Accounts, Computers, Printers,File Shares, Security Groups
- Centralized security management, create account, assign permissions
- Objects are organized in **trees**
- A group of trees is a **forest**

![3%20Directory%20Services/Untitled.png](3%20Directory%20Services/Untitled.png)

---

# AWS Directory Services

- **AWS Managed Microsoft AD**
    - Create your own AD in AWS, manage users locally, supports MFA
    - Establish “trust” connections with your on-premise AD

![3%20Directory%20Services/Untitled%201.png](3%20Directory%20Services/Untitled%201.png)

- **AD Connector**
    - Directory Gateway (proxy) to redirect to on-premise AD
    - Users are managed on the on-premise AD

![3%20Directory%20Services/Untitled%202.png](3%20Directory%20Services/Untitled%202.png)

- **Simple AD**
    - AD-compatible managed directory on AWS
    - Cannot be joined with on-premise AD

![3%20Directory%20Services/Untitled%203.png](3%20Directory%20Services/Untitled%203.png)