# 9. EBS vs EFS For Solutions Architect

- EBS volumes can be attached to only one instance at a time
- EBS volumes are locked at the AZ level
- Migrating an EBS volume across AZ means first backing it up (snapshot), then recreating it in the other AZ
- EBS backups use IO and you shouldn’t run them while your application is handling a lot of traffic
- Root EBS Volumes of instances get terminated by default if the EC2instance gets terminated. (you can disable that)
- Disk IO is high => Increase EBS volume size (for gp2)

    If you have IO1, you can just directly increase the IOPS right way.

- EFS mounting 100s of instances
- EFS share website files

    You want to share website files for being able to work with the wordpress

- EFS share website files

    EBS is going to be more like GP2, optimize on cost, and so it's going to be more for local type of storage on your EC2 instance.

- Custom AMI for faster deploy on ASG
- EFS vs EBS vs Instance Store
    - EFS: Network File System

        Hundreds of instances across AZs

        more expensive, really helpful when you need to share files across many instances.

    - EBS: going to be for local storage

        We want that local storage to be portable. If one EC2 fails, we want to be able to detach our volume, attach it onto another instance and we're done

    - Instance Store: actual physical volume on instance itself

        Ephemeral storage, cannot attach it and detach it on other instances. When we stop the instance, it's gone.

        Higher performance, but it doesn't have all this nice capability to remap it to other EC2 instances.