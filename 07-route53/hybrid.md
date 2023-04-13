## Endpoints
    - VPC interfaces ( ENIs) accessible over VPN and DX
    - Inboudn and Outbound
    - Inbound
        - Onn prem can forward to R53 resolver
    - Outbound
        - Conditional fwder, T53 -> On prem

## DNSSEC
    - Requires asymmetric keys - NEED to be US-East-1
    - Create alarms with DNSSECInternalFailure & DNSSECSigningKeysNeedingAction
    - DNSSEC Validation can be enabled for VPCs - invalid results mean zones wont be returned.