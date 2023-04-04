## IPsec VPN basics
    - Symmetric encrpytion - Fast, hard to exchange keys sucurely
    - Assymetric keys - slower - but easier to exchange keys ( public encrpyts, private decrytps)
    - 2 main phases
        - IKE phase 1 ( slow/heavy)
                - Auth ( eg. PSK/cert )
                - Use asymmetric enc to agree, then create a symmetric key
                - IKE SA created = Phase 1 tunnel
        - IKE Phase 2 ( Fast and agile)
                - Use keys from phase 1
                - Create IPSEC SA.. Phase 2 tunnel created.
    - Policy based VPNS (more tricky) - split tunneling
            - Rule sets to match traffic
    - Route based VPNS (simple)
            - Send routes ( prefixes) over VPN
    