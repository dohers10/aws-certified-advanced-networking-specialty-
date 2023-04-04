## General
    - Direct encrypted network link between 2 VPCs ( ONLY EVER 2)
    - same/cross region and same/cross account
    - Same ergion SGs can ref peeer SGs
    - VPC Peering is NOT transitive. Eg 3 VPCs cant talk through each other
    - no overlapping CIDR ranges allowed!
    - Always encrypted
    - cross region is AWS global transit network, not public internet
    - DNS options can be set, two options, Requester and Accepter
    - Both VCs must be enabled for DNS hostnames and DNS resolution for dns to be in place