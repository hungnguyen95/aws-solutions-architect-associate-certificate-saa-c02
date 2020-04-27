# 8. AWS Elastic Transcoder

- **Convert media files (video + music)** stored in S3 into various formats for tablets, PC, Smartphone, TV, etc
- Features: bit rate optimization, thumbnail, watermarks, captions, DRM, progressive download, encryption
- 4 Components:
    - Jobs: what does the work of the transcoder
    - Pipeline: Queue that manages the transcoding job
    - Presets: Template for converting media from one format to another
    - Notifications: SNS for example
- **Pay for what you use, scales automatically, fully managed (Serverless)**