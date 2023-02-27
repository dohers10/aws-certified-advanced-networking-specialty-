## Placement Groups
    - Cluster - Pack instances close together - HIGH performance!
        - launch into single AZ ( dont specify - frst one in decides) - cant span AZs
        - Same rack/sometimes same host
        - direct conns to each other - single stream transfer rates - good for performance! 10Gbps
        - lowest latency and max PPS poss in aws
        - CON - little/no resiliance
        - Can span VPC peers, does impact performance
        - Generaly use same instance and generally launch at same time


    - Spread - Keep instances seperate - Maximum amount of availability! 
        - 7 instances per AZ in each region!
        - Infra isolation - guaranteed
        - Diff rack, diff power, diff network
        - CANNOT use dedicated instances or hosts
        - small number of criticial instances that need to be seperated - think DCs etc..

    - Partitions - Groups of instances spread apart - HUGE scale paralell systems, clusters but seperated
        - divided partittions ( max 7 partitions each AZ) but many instances within partition
        - each partition is isolated but you can decide which AZ/partition
        - ..or you can allow EC2 to auto place
        - Great for topology aware apps such as HDFS, HBASE and Cassandara
        - Contain impact of failures, significant levels of resliance for LARGE orgs
