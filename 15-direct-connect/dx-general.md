## Concepts
        - physical connection - 1GB, 10GB or 100GB 
        - single-mode fiber... NO copper
        - 1000BASE-LX transeicver - 1 GBPS
        - 10GBASE-LR - 10gbps
        - 100GBASE-LR4 - 100GBPS
        - Auto-negotiation DISABLED
        - Port Speed and full duplex manually set


# VIFs
        - 3 types - private, public and transit
        - !! A dx GW can be associated with VPCs and Private VIFs OR TGW and Transit VIF... NOT BOTH!!

                - Private VIF
                        - Access to 1 VPC from on prem
                        - Generally attached to VGW  - w vpc only
                        - Same region as DX location your connection terminates in
                        - No encrpytion on private VIFs by default
                        - normal or jumbo frames fine - MTU of 1500/9001
                        - Allows Route propagation by default using VGW
                        - AW will advertise VPC CIDR and the BGP peer IPs ( /30s)
                        - You can advertise defaut or specific corp prefixes ( MAX 100). WIll kill the interface!
                        - - public owned ASN or own private ASN ( 64512 to 65535)

                - Publc VIF 
                        - Allows to connect to AWS Public services
                        - Can be used with IPSec to form a VPN ove public vpn to access PRIVATE services. Allows E2E encrpytion wiht low latency
                        - advertises public S3 range from ALL regions! Must be careful

                - Transit VIF
                        - only 1 transit VIF per DX
                        - Each VIF supports up to 3 TGWs
                         - Can be attached to up to 20DXGWs!


## BFD - Bidirectional Forwarding Detection
        - Improve Failover time - less than 1second
        - Liveness detection interval is 300ms
        - multiplier is 3 ( so as per above, would be 900ms to fail)
        - customer side cofig is rew.. BGP options

## BGP & BGP Communities
        - Think of as extra metadata... NO_EXPORT ( dont adv to external peers - AWS use for inbound).. NO_ADVERTISE ( adv to NO peers) etc
        - flexible routing
        - AWS - AS 7224 ASN
        - Create routing policy based on community tags
        - Local pref!


## DX Gateway
        - Global device
        - Any region private VIF top dx GW
        - 1 private VIF = 1 DX GW & 10 VGW per DW GW
        - 1 DX can have 50 private VIFS == 50 DX GWs == 500 VPCs
        - Allows DX GW to associatye to other VPCs etc.. 
        - Cannot route. So Eg. 2 TGWs to one DXGW .. Must use TGW peering
        - Cannot support routing between interfaces attached to DX GW( so even 2 on prem DX locations)

## LAG
        - Think SPEED! not resiliaant
        - active/active
        - all conns need to be the same speed
        - two 100GB ports or 4 ports if usnig less than 100GB. Max performance of 200GB!
