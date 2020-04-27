# 6. S3 Websites

- S3 can host static websites and have them accessible on the www
- The website URL will be:
    - `<bucket-name>.s3-website-<AWS-region>.amazonaws.com` ①
    - OR
    - `<bucket-name>.s3-website.<AWS-region>.amazonaws.com` ②

    → It depends on the region you're on, but overall, it looks like ②

- If you get a 403 (Forbidden) error, make sure the bucket policy allows public reads!