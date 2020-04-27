# 3. AWS S3 -Versioning

- You can version your files in AWS S3
- **It is enabled at the bucket level**

    → It's not profile settings, it's bucket level setting

- Same key overwrite will increment the “version”: 1, 2, 3….

    → For example: when you upload a file, it's version 1. Then you overwrite it, it's version 2, and so on...

- It is best practice to version your buckets
    - Protect against unintended deletes (ability to restore a version)
    - Easy roll back to previous version
- Any file that is not versioned prior to enabling versioning will have version “null”