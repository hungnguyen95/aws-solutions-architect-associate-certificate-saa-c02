# 9. MFA Delete

- MFA (multi factor authentication) forces user to generate a code on a device (usually amobile phone or hardware) before doing important operations on S3
- To use MFA-Delete, enable Versioning on the S3 bucket
- You will need MFA to
    - permanently delete an object version
    - suspend versioning on the bucket
- You won’t need MFA for
    - enabling versioning
    - listing deleted versions
- **Only the bucket owner (root account) can enable/disable MFA-Delete**
- MFA-Delete currently can only be enabled using the CLI