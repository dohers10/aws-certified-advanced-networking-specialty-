## IGW & NAT GW
    - 1to1 relationship to 1 VPC.
    - HA and scale by default
    - supports both IPv4 and IPv6 for inbound and outbound
    - IPv4 static 1to1 NAT
    - IPv6 no NAT, just fwds traffic
    - NAT GW - used for IPv4 for egress traffic ( doesnt allow inbound traffic). Doesn't suport IPv6
    - Egress IGW used for above use-case for IPV6 ONLY. Don't allow innbound

## BYOIP
    - Most specific IPv4 range you can BYO is /24, /48 for IPv6 for public and /56 for not public
    - One region at a time
    - 5 IPv4 and IPv6 address ranges per region per account
    - CANNOT share IP address range using RAM! 
    - can auth AWS to BGP advertise from ASN 16509 & 14618 ( Internet sees this as "within AWS")
    - Steps;
        1 & 2 - Key pair and Cert - prove who you are
        3 - Route Origin Authorisation ( ROA) - auth docuement to who can use this IP space and advertise in BGP
        4) RDAP record 
        5 & 6 - Provision and Advertise - proves/auths AWS to deploy
Example (keep in mind for exam Qs);
    aws ec2 provision-byo-up-cidr --cidr address-range --cidr-authorization-context Message="message",Signature="signature"
    or
    aws ec2 advertise-vyoip-cidr --cidr address-range

## Bastion Hosts
    - Server which runs at network edge
    - hardened to withstand attack from pubnlic network
    - Gatekeeper between zones ( public / private)

## NAT instance
    - Runs Linux AMI/NAT software on an EC2 instance
    - non specialised (eg. fast hardware)
    - good for low cost testing. Can fix cost using T3 micro for example
    - Need to disable src/dst check ( as IPs will be public/diff to EC2 eni expectation)
    - Can also be bastio host or do port forwarding - good cost saver for small use cases
    - one AZ/no resiliance ( scripts can be used to implement HA, update RTs to other NAT instance)
    - Can be used across DX, VPN or peering connection ( not ideal though)

## NAT GW
    - Used to allow private subnets to Internet
    - Sits in public subnet but not really public - uses private and IGW does translation. 1:1 to NAT
    - traffic hits NAT GW - uses transdlation table with src IP/ports. Translates to SRC ip of NATGW and dst of public IP
    - HA in specific AZ. If require full HA, need to deploy to all AZs UNLIKE IGW
    - 5gbps by default - Can scale up to 45gbps ( then can use multiple NATGWs for more). $ hourly charge + usage charge per GB - in addition to other services. 
    - Elastic IP cannot be changed on a NATGW. To change, need brand new NATGW
    -  Cannot be used across VPC peers, VPN or DX! Unlike NAt instance
    - handle 900 connections per second
    - ErrorPortAllocation error means you are at capacity - need to scale up etc
    - you would use gateway endpoints fo rs3/dynamoDB for low cost
    - CANNOT use sgs on natgw - diff to nat instance.
