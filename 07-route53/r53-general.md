## Hosted zones
    - Zone files in AWS/ hosted on 4 managed NS
    - Can be public - internet
    - can be private - linked to VPCs
    - hosts records ( recordsets)

## Record Types
    - Nameserver (NS)
    - A & AAAA records ( map host names to IP- IPv4/IPv6 respectively)
    - CNAME record type ( host to host records - can not resolve to IPS, only names)
    - MX records  ( Mail records)
    - TXT record - adds txt, the most common use case is to prove domain ownership. 

## Publich hosted zone
    - created auto when domain is registered via R53 - can be seperated seperately too
    - Hosts DNS records ( a, aaaa, mx, ns, txt etc)

## Private hosted zone
    - associated with VPCs and only accesible in those vpcs
    - split dns - overlapping public and private CAN be same zone name
    - Cannot be accessed outside of associated VPCs

## R53 alias
    - A maps to IP address
    - CNAME maps name to another name eg. netflix -> ww.netflix
    - cname is INVALID for naked/apex
    - Alias maps name to AWS resource
    - can be used for BOTH naked/apex AND normal records
    - NO charge for Alias requests pointing to aws resources
    - for any aws resources - default to picking ALIS
    - can have A record and CNAME alias
    - alias examples - API gw, clodufront, elastic beanstalk, ELB, global accelarator, S3

## R53 routing
    - Simple Routing ( think 1to1 )
            - 1 record per name
            - each record can have multiple values
            - eg. WWW = 1.2.2.3, 1.3.3.3, 1.4.4.4
                - When client looks up WWW, it receives ALL ips and client Chooses which to use
            - DOES NOT support health checks - the only one.
    - Failover Routing ( Think Active/Passive)
            - Primary/secondary
            - common example - primary poitns to EC2, secondary to S3 etc
            - Healthcheck on Primary
    - Multi-Value Routing (improved availability)
            - create multiple records with same name ( point to diff IPs as example)
            - Sends all values back to client to choose
            - HealthCheck on records, wont send any unhealthy ones to client
            - IMPROVES availability but NOT a replacement for LB
    - Weighted Routing ( simple lB or testing new SW versions)
            - Able to specify weight for each record, multiple records
                - Eg. 3 records, split 40 40 20. ( means first record returned %40 of the time, 40% thn %20)
            - weight of 0 means NEVER returned
            - unhealthy record will just be skipped ( but still selected)
    - Latency Routing (think performance and user expereince)
            - 3 records, diff regions, one record same name each region
                - keeps DB of latency, using IP lookup services
            - not REALTIOME
    - Geolocation Routing
            - location of resources & customers 
            - tag records with either Country, continent and/or "default" 
            - IP check verifies IP of user (normally resolver)
            - Doesnt return the closest record - ONLY the relevent records
            - checks in order -  State of USA, the country, the contintent - default ( the most specific) or NO ANSWER
    - Geo-Proximity ( think flexible and bias)
            - aims to calculate distance between customer and resource 
            - not same as latency as based on distance
            - lattitude/longitude can be used for external
                - eg. 3 resources UK,. USA, aus - can tag/define them on AWS region for AWS only, or lat/long for external.
            - '+' or '-' "bias" to increase or decrease regions, can manipulate where traffic goes. 
                - eg. could increase UK to be all of europe etc


## Healthchecls
    - seperate to records, health chcekcers are located globally
    - not just AWS - every 30 seconds by default or every 10s if pay extra $$
    - TCP, HTTP/HTTPs, HTTP/HTTPS with string matching
    - 2 states - healthy/unhealthy
    - Endpoint checks ( check health of endpoint)
    - CW alarms ( can be setup seperatley using CW agent)
    - Calculated - checks of other checks


