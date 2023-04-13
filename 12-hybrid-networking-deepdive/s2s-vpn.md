## General
        - Runs over internet, encrypted using IPSEC ( unles over DX!)
        - Full HA, if you design and implement correctly.
        - Quick to provision - under an hour.
        - Connect VPCs to onprem networks
        - VGW - logical obkect which could be used in route tables
        - CGW - Customer Gateway - logical piece of config in AWS. Thing it represents ( eg. physical on prem router)
        - to be FULLY HA, on prem needs a second router ( and pref a 2nd building)
        - Speed cap - 1.25GBps AWS limit
        - Latency - inconsistent, public internet could be bad
        - Hourly cost, GB out cost, data cap.
        - Backup to DX

## Static VPNs
    - Uses staticroutes etc
    - Simple, works with any router
    - Restricted for loadbalancing etc

## Dynamic VPNs
    - Needs BGP to route dynamically
    - More complex
    - Much more advanced features, load balancing etc. 
