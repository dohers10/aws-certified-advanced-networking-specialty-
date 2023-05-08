## General

        -Process real-time streaming data using Amazon Kinesis Data Stream. Integrate Amazon CloudFront with Lambda@Edge in order to process the data in close geographical proximity to users and respond to user requests at low latencies.

        -Amazon RDS supports using Transparent Data Encryption (TDE) to encrypt stored data on your DB instances running Microsoft SQL Server. TDE automatically encrypts data before it is written to storage and automatically decrypts data when the data is read from storage.
            -Amazon RDS Encryption just encrypts your Amazon RDS DB instances and snapshots at rest. It doesn’t automatically encrypt data before they are written to storage, nor automatically decrypt data when they are read from storage.

        In CloudFront, there are 3 options that you can choose as the value for your Origin Protocol Policy:
                - HTTP Only
                - HTTPS Only
                - Match Viewer.

                - the term “Viewer” in CloudFront basically means the requestor or the client that sends the request. Therefore, the name: “MatchViewer” basically means that CloudFront is simply matching the protocol being used by the viewer.
        
        
        - Autonomous System (AS) prepending doesn’t work if you use a private ASN for a public virtual interface. 

        - Amazon Inspector compares the behavior and the security configuration of the assessment targets to selected security rule packages.

If you are using NAT traversal (NAT-T) on your device, you must include rules that allow UDP access over port 4500. Check if your device is advertising NAT-T.

Hence, the correct answers are:

-Ensure that UDP over port 500 is allowed in the firewall to enable the transmission of Internet key exchange (IKE) packets

-Ensure that the IP Protocol 50 or the Encapsulating Security Payload (ESP) is allowed in the firewall to enable the transmission of IPsec packets that contain the encrypted network traffic.

-Allow UDP access over port 4500 in the firewall
- IPV6 NOT supported in VGW

## Continued 

BGP
If you’re using a public ASN:

-Confirm that your customer gateway is advertising the same prefix (public IP or network that you own) on both Border Gateway Protocol (BGP) sessions.

-You can use the BGP AS_Path attribute such that the prefixes advertised from the secondary connection are prepended with the customer gateway ASN twice. For example, if your customer gateway uses ASN 123, it can advertise the prefix on the secondary connection with AS_Path set to 123 123.

-You can use the BGP Local Preference attribute such that the customer gateway accepts routes from the primary connection as 200 and the secondary connection as 100. A higher Local Preference value is preferred, and the default is 100.

-The primary connection is considered the primary path. In the event of a failure, traffic is shifted to the secondary connection as a secondary path.

Influencing inbound traffic to on premises using local preference BGP community tags when the Direct Connect connections aren't located in the same AWS Region as the VPC
You can use local preference BGP community tags to achieve load balancing and route preference for incoming traffic to your network. These local preference BGP community tags are supported:

7224:7100 = Low preference
7224:7200 = Medium preference
7224:7300 = High preference

- Storage Gateway uses public endpoints!!


- Network Load Balancers use Proxy Protocol version 2 to send additional connection information, such as the source and destination. Proxy Protocol version 2 provides a binary encoding of the Proxy Protocol header. 
