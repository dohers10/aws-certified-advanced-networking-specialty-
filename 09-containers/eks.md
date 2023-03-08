## Kubernetes
    - Run containers in a reliable way. Like Docker but with intellegence.
    - Cluster control plane,. has cluster nodes (a VM/server that functions as worker)
    - Node - Resources ( pods are placed on nodes to run)
    - Job - ad-hoc, creates one or more pods until completion
    - Ingress - exposes a way into service
    - Use pods - smallest units of compute
    - kube-apiserver = the fronmt end for kubernetes control plane
    - etcd - HA key value store
    - kube-scheduler - identifies pods within cluser with no assigned nodes
    - cloud-controller-manager = integration with cloud like AWS/Azuer etc

## EKS
    - AWS Managed Kuberenetes - Open source and lcoud agnostic
    - Control plane scales + runs on multi AZ
    - Inegrates with other aws services - eg,. ECR, ELB, IAM, VPC
    - EKS Cluster = EKS Control plane + EKS Nodes
    - etcd - managed by AWS and multi AZ
    - Nodes = Self managed, managed node groups + Fargate pods
    - storage such as EBS, EFs, FSx, Lustre