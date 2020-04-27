# 5. AWS Cognito

- We want to give our users an identity so that they can interact with our application.
- **Cognito User Pools:**
    - Sign in functionality for app users
    - Integrate with API Gateway
- **Cognito Identity Pools (Federated Identity):**
    - Provide AWS credentials to users so they can access AWS resources directly
    - Integrate with Cognito User Pools as an identity provider
- **Cognito Sync:**
    - Synchronize data from device to Cognito
    - May be deprecated and replaced by AppSync

---

# AWS Cognito User Pools (CUP)

- Create a serverless database of user for your mobile apps
- Simple login: Username (or email) / password combination
- Possibility to verify emails / phone numbers and **add MFA**
- Can enable Federated Identities (Facebook, Google, SAML…)
- Sends back a JSON Web Tokens (JWT)
- **Can be integrated with API Gateway for authentication**

![5%20AWS%20Cognito/Untitled.png](5%20AWS%20Cognito/Untitled.png)

---

# AWS Cognito – Federated Identity Pool

- Goal
    - Provide direct access to AWS Resources from the Client Side
- How:
    - Log in to federated identity provider – or remain anonymous
    - Get temporary AWS credentials back from the Federated Identity Pool
    - These credentials come with a pre-defined IAM policy stating their permissions
- Example:
    - provide (temporary) access to write to S3 bucket using Facebook Login

![5%20AWS%20Cognito/Untitled%201.png](5%20AWS%20Cognito/Untitled%201.png)

---

# AWS Cognito Sync

- **Deprecated – use AWS AppSync now**
- Store preferences, configuration, state of app
- Cross device synchronization (any platform – iOS, Android, etc…)
- Offline capability (synchronization when back online)
- **Requires Federated Identity Pool in Cognito (not User Pool)**
- Store data in datasets (up to 1MB)
- Up to 20 datasets to synchronise