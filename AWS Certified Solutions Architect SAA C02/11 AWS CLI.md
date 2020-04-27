# 11. AWS CLI

# AWS CLI Configuration

- Configure access key and secret access key via `aws configure`

![11%20AWS%20CLI/Untitled.png](11%20AWS%20CLI/Untitled.png)

---

# AWS CLI ON EC2… THE BAD WAY

- We could run `aws configure` on EC2 just like we did (and it’ll work)
- But… it’s SUPER INSECURE
- **NEVER EVER EVER PUT YOUR PERSONAL CREDENTIALS ON AN EC2**
- Your **PERSONAL** credentials are **PERSONAL** and only belong on your **PERSONAL** computer
- If the EC2 is compromised, so is your personal account
- If the EC2 is shared, other people may perform AWS actions while impersonating you
- For EC2, there’s a better way… it’s called AWS IAM Roles

---

# AWS CLI ON EC2… THE RIGHT WAY

- IAM Roles can be attached to EC2 instances
- IAM Roles can come with a policy authorizing exactly what the EC2 instance should be able to do

![11%20AWS%20CLI/Untitled%201.png](11%20AWS%20CLI/Untitled%201.png)

- EC2 Instances can then use these profiles automatically without any additional configurations
- This is the best practice on AWS and you should 100% do this.

---

# AWS EC2 Instance Metadata

- AWS EC2 Instance Metadata is powerful but one of the least known features to developers
- It allows AWS EC2 instances to ”learn about themselves” **without using an IAM Role for that purpose.**
- The URL is [`http://169.254.169.254/latest/meta-data`](http://169.254.169.254/latest/meta-data)
- You can retrieve the IAM Role name from the metadata, but you CANNOT retrieve the IAM Policy.
- Metadata = Info about the EC2 instance
- Userdata = launch script of the EC2 instance

---

# AWS SDK Overview & Credentials Security

- the AWS CLI uses the Python SDK (boto3)
- It’s recommend to use the **default credential provider chain**
- The **default credential provider chain** works seamlessly with:
    - AWS credentials at ~/.aws/credentials (only on our computers or on premise)
    - Instance Profile Credentials using IAM Roles (for EC2 machines, etc…)
    - Environment variables (AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY)
- **Overall, NEVER EVER STORE AWS CREDENTIALS IN YOUR CODE**
- **Best practice is for credentials to be inherited from mechanisms above, and100% IAM Roles if working from within AWS Services**

## Exponential Backoff

- Any API that fails because of too many calls needs to be retried with Exponential Backoff
- These apply to rate limited API
- Retry mechanism included in SDK API calls

![11%20AWS%20CLI/Untitled%202.png](11%20AWS%20CLI/Untitled%202.png)

⇒ If your API calls still keep on failing, we will wait twice as long as the previous API call to try again.

⇒ Ensure that you don't overload the API by trying it every millisecond.