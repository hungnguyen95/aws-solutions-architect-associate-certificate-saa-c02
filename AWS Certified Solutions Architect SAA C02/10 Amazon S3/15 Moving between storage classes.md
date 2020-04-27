# 15. Moving between storage classes

- You can transition objects between storage classes
- For infrequently accessed object, move them to `STANDARD_IA`
- For archive objects you don’t need in real-time, `GLACIER` or `DEEP_ARCHIVE`
- Moving objects can be automated using a **lifecycle configuration**

![15%20Moving%20between%20storage%20classes/Untitled.png](15%20Moving%20between%20storage%20classes/Untitled.png)

---

# S3 Lifecycle Rules

- **Transition actions**: It defines when objects are transitioned to another storage class.
    - Move objects to Standard IA class 60 days after creation
    - Move to Glacier for archiving after 6 months
- **Expiration actions**: configure objects to expire (delete) after some time
    - Access log files can be set to delete after a 365 days
    - **Can be used to delete old versions of files (if versioning is enabled)**
    - Can be used to delete incomplete multi-part uploads
- Rules can be created for a certain prefix (ex - `s3://mybucket/mp3/*`)
- Rules can be created for certain objects tags (ex - `Department: Finance`)

## Lifecycle Rules – Scenario 1

- Your application on EC2 creates images thumbnails after profile photos are uploaded to Amazon S3. These thumbnails can be easily recreated, and only need to be kept for 45 days. The source images should be able to be immediately retrieved for these 45 days, and afterwards, the user can wait up to 6 hours. How would you design this?

- S3 source images can be on STANDARD, with a lifecycle configuration to transition them to GLACIER after 45 days.
- S3 thumbnails can be on ONEZONE_IA, with a lifecycle configuration to expire them (delete them) after 45 days.

## Lifecycle Rules – Scenario 2

- A rule in your company states that you should be able to recover your deleted S3 objects immediately for 15 days, although this may happen rarely. After this time, and for up to 365 days, deleted objects should be recoverable within 48 hours.

- You need to enable S3 versioning in order to have object versions, so that“deleted objects” are in fact hidden by a “delete marker” and can be recovered
- You can transition these “noncurrent versions” of the object to S3_IA
- You can transition afterwards these “noncurrent versions” to DEEP_ARCHIVE

##