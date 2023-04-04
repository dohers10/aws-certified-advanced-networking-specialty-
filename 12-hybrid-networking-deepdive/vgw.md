## General
        - Virtual Private Gateway
        1 VPC at a time
        - Uses BGP with default ASN of 64512
        - HA by defauklt
        - public IPs when connecting to VPNs
        -  Can connect to DX but ONLY if same region
        - Can use route propagation
        - Allo wfor Route propogation into subnet RTs ( eg BGOP routes learnt will be automatically added) UNLIKE Transit GW
        - Dynamic VPNs can act as backups for DX. Dynamic routes preferrede vs dynamic VPN
        - Can attach/detach/attach VGW to multiple VPCs ( but only ever 1 at one time!)
        - VPN CloudHub - can create a hub spoke network to multiple VPNS ( with VGW as hub - remote sites with unique BGP ASN are spokes)
                        - All need to terminate into VGW with unique CIDR ranges
                        - Dynamic S2S vpns created between multuiple customer sites and the VGW.