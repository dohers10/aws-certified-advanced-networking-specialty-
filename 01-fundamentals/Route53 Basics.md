# Route53 basics
- Two main functions
    - Register Domains
    - Host Zones
- Global service
- Globally resiliant

## Register Domains
When a domain is registered a few things happen:
    - Route 53 checks with the registry for the top-level domain if the domain is available
    - Route 53 creates a zone file for the domain
    - Route 53 allocates NS with the zone (4 managed nameservers for a hosted zone)
    - It communicates with the top-level registry and adds the nameserver records into the zone file for top-level domain

## Record Types
    - Nameserver (NS)
    - A & AAAA records ( map host names to IP- IPv4/IPv6 respectively)
    - CNAME record type ( host to host records - can not resolve to IPS, only names)
    - MX records  ( Mail records)
    - TXT record - adds txt, the most common use case is to prove domain ownership. 

