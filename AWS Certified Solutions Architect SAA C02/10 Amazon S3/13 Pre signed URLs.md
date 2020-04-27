# 13. Pre-signed URLs

- Can generate pre-signed URLs using SDK or CLI
    - For downloads (easy, can use the CLI)
    - For uploads (harder, must use the SDK)
- Valid for a default of 3600 seconds, can change timeout with `--expires-in [TIME_BY_SECONDS]` argument
- Users given a pre-signed URL inherit the permissions of the person who generated the URL for GET / PUT
- Examples :
    - Allow only logged-in users to download a premium video on your S3 bucket
    - Allow an ever changing list of users to download files by generating URLs dynamically
    - Allow temporarily a user to upload a file to a precise location in our bucket