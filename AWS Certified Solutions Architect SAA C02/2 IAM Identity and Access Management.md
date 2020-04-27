# 2. IAM (Identity and Access Management)

- Your whole AWS security is there:
    - Users
    - Group
    - Roles
- Root account should never be used (and shared)
- Users must be created with proper permissions
- IAM is at the center of AWS
- Policies are written in JSON (JavaScript Object Notation)

![2%20IAM%20Identity%20and%20Access%20Management/Untitled.png](2%20IAM%20Identity%20and%20Access%20Management/Untitled.png)

- IAM has a global view
- It's best to give users the minimal amount of permissions they need to perform their job (lease privilege principles)
- One IAM **User** per PHYSICAL PERSON
- ONE IAM **Role** per Application
- IAM credentials should NEVER BE SHARED
- Never write IAM credentials in code
- Never commit your IAM credentials
- Never use ROOT IAM Credentials