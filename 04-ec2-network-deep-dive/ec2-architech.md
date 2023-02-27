## Advanced EC2 networking
    - Primary ENI cannot be moved/removed
    - Secondary ENi can be removed/moved and used with diff access ( think FTD)
    - CAN have multiple subnets on ENIs ( Just not cross AZ!!)
    - SGs associated to ENI not EC2
    - ENi can be moved between EC2!
    - Public IP assigned ( if enabled) assigned to INSTANCE, cannot be seen by OS
    - NO use case for public IP on an ENI
    - Associating elastic IP to EC2, does it to primary eni
    - Elastic IPs not charged if in use BUT do cost when not being used or instance down
    - IPV6 publicly routable, so is assigned to ENI and OS does know about it
    - SRC/DST check is on by default - drops packet if src/dst address isnt on that ENI.
    - Multiple ENI scenarios - MGMT/isolated networks, Software licensing ( MAC), Sec/Network appliances like FWs, multi-homed instances with workloads/roles in diff subnets & low budget/simple HA solution.

## Enhanced Netowrking ( SR-IOV)
    - VMs traditionally share physical NIC, hypvervisor mediates access ( slow)
    - Passthrough as an option - 1 VM <-> 1 NC
            - Great performance as near bare metal ( 1:1 mapping between VM and physical)
            - Bad for HA - The VM now dependent on physical hardware, cant scale!
    - SR-IOV as option .. Many VMs <-> 1 NIC, faster speeds, low cpu at higher loads etc ( no hypervisor needed). suported on almost all types of EC2 instances
            - "Enhanced networking"
            - ENis have VF ( Virtual Functions) - think mini NICs!
                - CMs access VF directly resulting in near bare metal performance, 1 physical device offer 256  VFs!
                - VFs can be used independently with no hypervisor invlvement so fast/lisst to no CPU
    - Elastic Network Adaapter( ENA) up to 100GB
    - same region full nadwidth available to slowest instance. Diff regiong - aggregate BW quota of 5gb
    - 5 Tuple limit - 5Gbps MAX. Multi-path TCP (MPTCP ) = full nabdwidth

## Elastic Fabric Adapter (EFA)
    - Think HPC ( high performance compute) or ML ( machine learning)!
    - type of ENI for EC2
    - 1 per instance
    - added at launch of when shutdown 
    - supports OS bypass (improves performance) 
        - SINGLE subnet only
        - OS bypass CANNOT be routed
        - SG needs an ALLOW all, self referential rule inbound & outbound.
    - Good for HPC or ML app - > OSI model, want app later <---> app layer talking quickly
    - Anything using MPI or NCCL
    - no OSI fluff ( no OS involvment, limited kernal involvment etc)