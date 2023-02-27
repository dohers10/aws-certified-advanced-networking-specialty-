## IPv6
    - Needs to be enabled at VPC level
    - Can use BYOP ip or AWS allocated /56 range ( entierly unique)
    - routing handled seperatly to IPv4 but same RT
    - if want only egress traffic ( like NAT GW in IPv4) then need to use an egress only IGW
    - Can have both IGW and egress only IGW attached to VPC to allow bi-directional traffic for IPv4/IPv6
    - Can migrate exisiting ipv3 VPC to IPV6 
    - Not everything within AWS suport IPV6 ( eg. privatelink)