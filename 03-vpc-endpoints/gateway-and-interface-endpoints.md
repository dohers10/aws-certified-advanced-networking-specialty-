## Gateway Endpoints
    - S3 and DynamoDB private only access
    - when associate, it adds a prefix list to RTs 
    - HA across all AZs by default
    - Endpoint olicy used to control what it can access.
    - Regional - can't access cross-region services
    - S3 bucket policy - only accept ops from Gateway endpoint, explicit deny kicks in for rest
    - Only accesible from inside that VPC.

## Interface Endpoints
    -  Private access to AWS public services
    - added to specific subnet - an ENI - NOT HA by default across al AZs. Need to deploy in each Az
    - Can support SGs for network
    - Endpoint policy still able
    - TCP and IPv4 only - not IPv6!
    - Uses Privatelink
    - multiple DNS names
            - Regional DNS
            - Zonal DNS
    - PrivateDNS - overrides the default dns for services, allows apps to use endpoints.
    - apply a deny on endpoint policy -> denies same VPC traffic as hits VPC but not local machine which bypasses that
