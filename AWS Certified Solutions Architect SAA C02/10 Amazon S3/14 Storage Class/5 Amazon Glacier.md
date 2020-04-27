# 5. Amazon Glacier

- Low cost object storage meant for archiving / backup
- Data is retained for the longer term (10s of years)
- Alternative to on-premise magnetic tape storage
- Average annual durability is 99.999999999%
- Cost per storage per month ($0.004 / GB) + retrieval cost
- Each item in Glacier is called “**Archive**” (up to 40TB)
- Archives are stored in ”**Vaults**”

---

# Amazon Glacier & Glacier Deep Archive

- Amazon Glacier – 3 retrieval options:
    - Expedited (1 to 5 minutes)
    - Standard (3 to 5 hours)
    - Bulk (5 to 12 hours)
    - Minimum storage duration of 90 days

- Amazon Glacier Deep Archive – for long term storage – cheaper:
    - Standard (12 hours)
    - Bulk (48 hours)
    - Minimum storage duration of 180 days