## Volume Gateway
    - normally a VM onprem
    - bridge between onprem stoarge and aws - presents it using iSCSO, NFS or SMB
    - used for things like migrations to AWS, extensions to AWS, Stoarge tiering, help with DR and replacement of backup systems

        - Stored mode
                - All stored locally/on prem, uses storage gateway endpoint -> EBS snapshots
                - Great for full fisk backups of servers
                - Great for DR - EBS snapshots can be used to create EBS voolumes.
                - DOESNT imporove DC capacity.. Main copy is stored on the gateway

        - Cached mode
                - NOT stored on premise - primary data stored in AWS/S3 - uses storage gateway endpoint -> S3 not EBS
                - AWS managed area of S3, not customer side.
                - only thing stored locally is cached data
                - Great for DC extension! HElps with capacity

## Tape Gateway (VTL)
    - tldr - virtual tape library in AWS
    - uses storage gateway endpoint, uses S3/Glacier
    - Great for using exisitng backup stuff but replacing the tape side of things
    - Can be used for migration - can keep historical set of backups whilst decom on prem equipment

## File mode
    - bridges on prem file storage and S3
    - Mount points ( shares) available via NFS ( linux etc) or SMB ( windows)
    - Files stored in a mount point, they are visible in an S3 bucket
    - S3 objects visibile as on prem files and vice versa! Structure is maintained
    - Primary data is held in S3 ! Cached onprem for performance
            - this allows integration with things like lambda etc
    - Multiple contrivbutors allows - eg 2 DCs
            - Doesnt suport objkect locking, can result in data loss
    - Replication
            - cross region replication