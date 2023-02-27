## General VPC (Custom VPC)
    - Regional service
    - Nothing IN or OUT without explicit config
    - Default or Dedicated Tenancy option. 
        - Default allows resources to be either shared or dedicated
        - Dedicated means all resources are dedicated with no choice.
    - Minimum /28 CIDR ( 16 IPs )
    - Maximum /16 CIDR ( 65,536 )
    - IPV6 - uses /56 CIDR block
    - DNS ip is Base ip + 2 
            - enableDnsHostnames - If TRUE - Gives instances with public IPs public DNS names
            - enableDnsSupport - Enables DNS resolution in vpc

## General Subnets
    - 1 subnet - 1 AZ 
    - 1 AZ > subnets
    - subnets cannot overlap
    - subnets within VPC speak to each other by default
    - 5 IPs reserved in every subnet ( eg. 10.16.16.0/20)
            - Network adresss ( eg. 10.16.16.0)
            - VPC Router | network + 1 (eg. 10.16.16.1)
            - DNS server/router | +2 (10.16.16.2)
            - Reserved future use | +3 ( 10.16.16.3)
            - Broadcast Adress | Last IP ( 10.16.31.255)
    - Auto Assign Public IPv4 subnet option 
    - Auto assign IPv6
    - DHCP options set 
            - Immutable/cannot edit
            -  Max 1 assigned to VPC
            - When you changeover - its immediate but only affects clients when DHCP renew occurs
    - associate with 1 RT only. If remove custom RT, auto assigns default RT.


## VPC Router
    - HA across all AZs
    - Subet+1 is the interface into each subnet

## NACLs
    - Default NACL with vpc allows all
    - Custom default denies all
    - Explicity allow and deny


## SGs
    - Attached only to ENIs ( not instances etc)
    - Cannot explicitly block traffic
    - Ref a SG, refers to any resource that has that SG associated. Great for scaling and simplifies.
    - Self referencing - allows all internal trafic to each other ( eg ASG with 30 instances can speak to each other)



