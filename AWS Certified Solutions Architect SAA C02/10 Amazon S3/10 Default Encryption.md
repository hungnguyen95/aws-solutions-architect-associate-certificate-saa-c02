# 10. Default Encryption

- The old way to enable default encryption was to use a bucket policy and refuse any HTTP command without the proper headers:

![10%20Default%20Encryption/Untitled.png](10%20Default%20Encryption/Untitled.png)

- The new way is to use the “default encryption” option in S3
- Note: Bucket Policies are evaluated before “default encryption”