## Directory Service
        - NATIVE Microsoft Microsoft AD 2012
        - standard AD tools
        - Supports group poliyc and SSO
        - 2 sizes - standard ( 30k ) & Enterprise ( 500k)
        - Used for AD authentication and authorization
        - 2AZ+ by default ( HA)
        - Supports 1 way and 2 way external and forest trust with on-prem AD
        - Directory in AWS -> Means if DX link dies etc, its capable of running independently
        - supports radius-based MFA
        - Best to use this for 5000 users + and if yuou need trust relationships between AWS and on prem directories
        - Auto patching and mainteannce
        - FULL DIRECTORY mode means full directory in AWS - own users, objects, can support any AWS services which support AD. egg. workspaces, RDS, chime, connect..
        - Trusts and Schemas extensions supported in this mode ONLY

## AD Connector
        - Pair of directory endpoints runnnig n AWS ( ENIs in a VPC)
        - redirects request to EXISTING directory servers on prem
        - no directory data stored in AWS... all redirected
        - Can use exisiting on prem AD for all compatible AWS services ( eg workspaces, rds, chime, connect)
        - Good for POCs, where you need to use existing identities.
        - 2 sizes - small/large. no explicit limits, just bases on compute/performance
        - Multiple connectors can be used to spread load
        - Req 2 subnets within vpc./diff Azs
        - at least 1 SD on prem ( normally 2)
        - Req working network connection ( dx/s2s vpn etc)
        - good for POC, business small infrastrucute in cloud or compliance cant store on AWS
        - no networks - things BREAK!