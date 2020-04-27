# 2. AWS S3 Overview - Objects

- Objects (files) have a Key. The key is the **FULL** path:
    - <my_bucket>/my_file.txt
    - <my_bucket>/my_folder1/another_folder/my_file.txt
- There’s no concept of “directories” within buckets (although the UI will trick you to think otherwise)
- Just keys with very long names that contain slashes (“/”)
- Object Values are the content of the body:
    - Max Size is 5TB
    - If uploading more than 5GB, must use "multi-part upload"
- Metadata (list of text key / value pairs – system or user metadata)
- Tags (Unicode key / value pair – up to 10) – useful for security / lifecycle
- Version ID (if versioning is enabled)