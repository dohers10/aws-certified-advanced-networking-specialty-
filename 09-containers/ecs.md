## General
    - EC2 mode and Fargate
    - Create clusters where containers run from
    - ECR/ Elastic Container Registry - container registry (similar to dockerhub)
    - Container definition -> container IMAGE & which port exposed
    - Task definition -> Self contained application. Could be 1 container or many.
        -> Represents application as a whole
        -> HOW things are ran
        -> Stores reources like CPU, networking mode, compatability (eg. ec2 mode or fargate) and Task role.
    - Task role -> IAM role that can be assumed, allows it to interact with other AWS resources. Think Security.
    - ECS Service
        -> Configured via service definiation
        -> How to scale/Can add HA/ restarts.

## ECS Cluster types
    - Both modes share SchedulingAndOPrchestration/ClusterManager/PlacementEngine

    - EC2 mode
        -ECS cluster created within VPC
        - Multi AZ beneftis
        - EC2 instances run containers
        - ASG controls the scaling for EC2
        - you pay for EC2, not serverless. Even if nothing happening on them.
        - Need to worry about capacity and cost.
        - Can use ECR
    
    - Fargate mode
        - Serverless!
        - Can use ECR
        - Uses Cluster within VPC
        - ECS tasks are within the Fargate SHAREd infra .. However tasks are injected INTO vpc and is given Elastic IP
        - Can still talk to private/public IPs
        - You only pay for container resources that you use -> unlike EC2 mode

## EC2 vs ECS(EC2) vs Fargate -> When to use each?!
    - If you use containers.. pick ECS
    - Large workload and price conscious... Use ECS (ec2 mode), then use spot instances etc
    - Large worklaod and Overhead conscious .. Use Fargate , minimises mgmt overhead
    - Small/Burst workloads... Fargate
    - Batch/Periodic workloads... Fargate

