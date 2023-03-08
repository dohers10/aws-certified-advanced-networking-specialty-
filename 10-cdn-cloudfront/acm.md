
## ACM
    - Can be public or private CA
    - Private CA - Apps need to trust your CA.
    - Public CA - Browsers trust a list of providers, whcih can trust other providers ( establishes chain of trust)
    - Can generare or import Certs
    - Can auto-renew when generated.
    - Can NOT auto-renew for imported
    - Certs can only be deployeed to supported services.. Eg. Cloudfront and ALB... NOT EC2 !
    - ACM is REGIONAL
    - Certs cannot leave the region they are generated or imported in
            - To use a cert with an ALB in ap-southeast-2  you NEED a cert in ACM in ap-southeast-2
            - 1 exception ( kind of)..Cloudfront is global but based in us-east-1, so CERT must be in us-east-1