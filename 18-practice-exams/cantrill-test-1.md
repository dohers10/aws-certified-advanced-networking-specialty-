- DNS Alias record
    -> Cost benefits?

-> create an account
        ->vpc per region
        - public subnet per region?
            - IGW per subnet?!

--> Reminder, S2S VPN 1.5GB. 10GB internet connection and best performance means setting up MULTIPLE S2S vpn conns and using ECMP

--> Access SNS and S3 in diff ergions via DX... Single public VIF can access all services.

--> ensure each  DX connection can access public AWS services in that region only
        -> config a filter for 7224:8100 BGP community
                    -> 7224:8100—Routes that originate from the same AWS Region in which the AWS Direct Connect point of presence is associated.