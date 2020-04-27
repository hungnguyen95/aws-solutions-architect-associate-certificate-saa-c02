# 2. Identity Federation & Cognito

# Identity Federation in AWS

- Federation lets users outside of AWS to assume temporary role for accessing AWS resources.
- These users assume identity provided access role.
- Federations can have many flavors:
    - SAML 2.0
    - Custom Identity Broker
    - Web Identity Federation with Amazon Cognito
    - Web Identity Federation without Amazon Cognito
    - Single Sign On
    - Non-SAML with AWS Microsoft AD

![2%20Identity%20Federation%20Cognito/Untitled.png](2%20Identity%20Federation%20Cognito/Untitled.png)

- **Using federation, you don’t need to create IAM users (user management is outside of AWS)**

---

# SAML 2.0 Federation

- To integrate Active Directory / ADFS with AWS (or any SAML 2.0)
- Provides access to AWS Console or CLI (through temporary creds)
- No need to create an IAM user for each of your employees

![2%20Identity%20Federation%20Cognito/Untitled%201.png](2%20Identity%20Federation%20Cognito/Untitled%201.png)

---

# SAML 2.0 Federation – Active Directory FS

- Same process as with any SAML 2.0 compatible IdP

![2%20Identity%20Federation%20Cognito/Untitled%202.png](2%20Identity%20Federation%20Cognito/Untitled%202.png)

---

# SAML 2.0 Federation

- Needs to setup a trust between AWS IAM and SAML (both ways)
- SAML 2.0 enables web-based, cross domain SSO
- Uses the STS API: AssumeRoleWithSAML
- Note federation through SAML is the “old way” of doing things
- **Amazon Single Sign On (SSO)** Federation is the new managed and simpler way

---

# Custom Identity Broker Application

- Use only if identity provider is not compatible with SAML 2.0
- **The identity broker must determine the appropriate IAM policy**
- Uses the STS API: `AssumeRole` or `GetFederationToken`

![2%20Identity%20Federation%20Cognito/Untitled%203.png](2%20Identity%20Federation%20Cognito/Untitled%203.png)

---

# Web Identity Federation – AssumeRoleWithWebIdentity

- Not recommended by AWS –use Cognito instead (allows foranonymous users, datasynchronization, MFA)

![2%20Identity%20Federation%20Cognito/Untitled%204.png](2%20Identity%20Federation%20Cognito/Untitled%204.png)

---

# AWS Cognito

- **Goal**
    - Provide direct access to AWS Resources from the Client Side
- **How**:
    - Log in to federated identity provider – or remain anonymous
    - Get temporary AWS credentials back from the Federated Identity Pool
    - These credentials come with a pre-defined IAM policy stating their permissions
- **Example**:
    - provide (temporary) access to write to S3 bucket using Facebook Login

![../16%20Serverless/5%20AWS%20Cognito/Untitled%201.png](../16%20Serverless/5%20AWS%20Cognito/Untitled%201.png)