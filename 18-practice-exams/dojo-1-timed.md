60%

- Region deny control -> Used in Control Tower
        - Used so that your end-users do not have permission to connect to a VPC in a Region that’s supported by AWS Control Tower but outside your governed Regions

- EKS - review
    - The instance is in a peered VPC
        -> If you have instances in a VPC that is peered with the load balancer VPC, you must register them with your load balancer by IP address, not by instance ID


RDS + Elastic beanstalk
    - You can use Secure Socket Layer (SSL) or Transport Layer Security (TLS) from your application to encrypt a connection to a DB instance running MySQL, MariaDB, SQL Server, Oracle, or PostgreSQL. Each DB engine has its own process for implementing SSL/TLS.
            - to setup SSL end to end encryption
                    -> Configure the Elastic Beanstalk environment’s EC2 instances to terminate the SSL/TLS connection for RDS. Modify the load balancer to use TCP and set the RDS to accept only SSL connections by using the GRANT command with the REQUIRE SSL option.

Secondary VPC
        If your primary CIDR block is publicly routable (non-RFC 1918), or if it is a CIDR block from the 100.64.0.0/10 range, then you are restricted to associating CIDR blocks from the RFC 1918 or the 198.19.0.0/16 range.

        Conversely, if your primary CIDR block is in the 10.0.0.0/8 range, then you are restricted from associating CIDR blocks with other RFC 1918* ranges (172.16.0.0/12 and 192.168.0.0/16).

DX cannot be upgraded - if want to move to higher GB, must be moved.

