# 4. EBS Migration

- EBS Volumes are only locked to a specific AZ
- To migrate it to a different AZ (or region)
    - Snapshot the volume
    - (optional) Copy the volume to a different region
    - Create a volume from the snapshot in the AZ of your choice