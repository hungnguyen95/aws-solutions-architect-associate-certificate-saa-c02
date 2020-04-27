# 7. AWS Opsworks

- Chef & Puppet help you perform server configuration automatically, or repetitive actions
- They work great with EC2 & On Premise VM
- AWS Opsworks = Managed Chef & Puppet
- It’s an alternative to AWS SSM
- No hands on here, no knowledge of chef and puppet needed
- **In the exam: Chef & Puppet needed => AWS Opsworks**

---

# Quick word on Chef / Puppet

- They help with managing configuration as code
- Helps in having consistent deployments
- Works with Linux / Windows
- Can automate: user accounts, cron, ntp, packages, services…
- They leverage “Recipes” or ”Manifests”
- Chef / Puppet have similarities with SSM / Beanstalk / CloudFormation but they’re open-source tools that work cross-cloud