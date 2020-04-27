# EC2 Instance Types

- R: applications that needs a lot of RAM – in-memory caches

    → in-memory caches or in-memory databases

- C: applications that needs good CPU – compute / databases

    → you have databases usually or applications with a lot of computations such as Big Data

- M: applications that are balanced (think “medium”) – general / web app

    → middle, medium: it's between RAM and between CPU (web apps or something very general)

- I: applications that need good local I/O (instance storage) – databases

    → a lot of disc operations, this is a database you are going to need

- G: applications that need a GPU – video rendering / machine learning

    → video rendering or machine learning

- T2 / T3: burstable instances (up to a capacity)

    → you get good performance for a burst (short while), but if you over abuse that burst, you'll lose that burst and lose your capacity

- T2 / T3 - unlimited: unlimited burst

    → give you unlimited burst

    [Burst Instances (T2/T3)](EC2%20Instance%20Types/Burst%20Instances%20T2%20T3.md)

Real-world tip: use [https://www.ec2instances.info](https://www.ec2instances.info/)