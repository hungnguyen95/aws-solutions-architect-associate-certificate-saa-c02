# 2. Reserved (MINIMUM 1 YEAR)

Run instance for a known amount of time (e.g you know that at least for one year you're going to need an EC2 instance) → use reserved instance type

### Reserved have **3 Types:**

- **Reserved Instances:** long workloads
- **Convertible Reserved Instances:** long workloads with flexible instances

    Instead of saying you want an m4.xlarge for 1 year, you're saying I want something for one year and you can convert what that something is. So maybe it's an m4.xlarge today, but maybe it's gonna be a c5.large tomorrow.

- **Scheduled Reserved Instances:**

    You wanna have instance every Thursday between 3p.m and 6p.m. Other than that you don't need it, but I know I will need this for at least a year.

---

- Up to 75% discount compared to On-demand
- Pay upfront for what you use with long term commitment
- Reservation period can be 1 or 3 years
- Reserve a specific instance type
- Recommended for steady state usage applications (think database)
- **Convertible Reserved Instances:**
    - can change the EC2 instance type
    - Up to 54% discount
- **Scheduled Reserved Instances:**
    - Launch within time window you reserve
    - When you require a fraction of day / week / month