# AMI (Amazon Machine Image)

- As we saw, AWS comes with base images such as:
    - Ubuntu
    - Fedora
    - RedHat
    - Windows
    - Etc ...
- These image can be customized at runtime by EC2 User data
- We want to create our own image that's ready  to go and to use instead of reproducing all that setup, all the time → That's called AMI and we can create AMI for our machines to use and it'll be custom AMIs

    ⇒ **That’s an AMI – an image to use to create our instances**

- AMIs can be built for Linux or Windows machines

---

## Why would you use a custom AMI?

- Using a custom built AMI can provide the following advantages:
    - Pre-installed packages needed
    - Faster boot time (no need for ec2 user data at boot time)
    - Machine comes configured with monitoring / enterprise software
    - Security concerns – control over the machines in the network
    - Control of maintenance and updates of AMIs over time
    - Active Directory Integration out of the box
    - Installing your app ahead of time (for faster deploys when auto-scaling)
    - Using someone else’s AMI that is optimized for running an app, DB, etc…
- **AMI are built for a specific AWS region (!)**

---

## Using Public AMIs

- You can leverage AMIs from other people
- You can also pay for other people’s AMI by the hour
    - These people have optimized the software
    - The machine is easy to run and configure
    - You basically rent “expertise” from the AMI creator
- AMI can be found and published on the Amazon Marketplace
- Warning:
    - Do not use an AMI you don’t trust!
    - Some AMIs might come with malware or may not be secure for your enterprise

---

## AMI Storage

- Your AMI take space and they live in Amazon S3
- Amazon S3 is a durable, cheap and resilient storage where most of your backups will live (but you won’t see them in the S3 console)
- By default, your AMIs are private, and locked for your account / region
- You can also make your AMIs public and share them with other AWS accounts or sell them on the AMI Marketplace

---

## AMI Pricing

- AMIs live in Amazon S3, so you get charged for the actual space in takes in Amazon S3
- Amazon S3 pricing in US-EAST-1:
    - First 50 TB / month: $0.023 per GB
    - Next 450 TB / month: $0.022 per GB
- Overall it is quite inexpensive to store private AMIs
- Make sure to remove the AMIs you don’t use

---

## Cross Account AMI Copy (FAQ + Exam Tip)

- You can share an AMI with another AWS account
- Sharing an AMI does not affect the ownership of the AMI

    → If you share AMI with someone else's account, you still own the AMI

- If you copy an AMI that has been shared with your account, you are the owner of the target AMI in your account.

    → Ex: User **A** has shared to **B** a AMIs. If **B** copy it into another region, then **B** become the owner of that AMI in that region.

- To copy an AMI that was shared with you from another account, the owner of the source AMI must grant you read permissions for the storage that backs the AMI, either the associated EBS snapshot(for an Amazon EBS-backed AMI) or an associated S3 bucket (for an instance store-backed AMI).

    ![AMI%20Amazon%20Machine%20Image/Untitled.png](AMI%20Amazon%20Machine%20Image/Untitled.png)

    → But it doesn't prevent fully copying AMI (just prevent directly copying AMI). There is a way that if someone launches an EC2 instance from an AMI you own, and then makes a AMI from that EC2 instance, basically they'll be able to create and effectively copy your AMI.

- **Limits:**
    - You can't copy an encrypted AMI that was shared with you from another account. Instead, if the underlying snapshot and encryption key were shared with you, you can copy the snapshot while re encrypting it with a key of your own. You own the copied snapshot, and can register it as a new AMI

    → Ex: User **A** has made a AMI and encrypted it with KMS as snapshot. And user **A** shared KMS and encrypted snapshot to user **B**. User **B** access to this snapshot, use **A**'s KMS to decrypt and use his KMS (**B**'s KMS) to re-encrypt this snapshot. Now user **B** make a AMIs from new encrypted snapshot.

- You can't copy an AMI with an associated billingProduct code that was shared with you from another account. This includes Windows AMIs and AMIs from the AWS Marketplace. To copy a shared AMI with a billingProduct code, launch an EC2 instance in your account using the shared AMI and then create an AMI from the instance.

### Reference:

[https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/CopyingAMIs.html](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/CopyingAMIs.html)