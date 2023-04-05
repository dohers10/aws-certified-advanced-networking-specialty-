## General
    - optimise flow of data from user to AWS
    - utilise anycast IPs ( 2 of em)
    - eg, unicast public IP of 1.2.3.4 - edge locations around world, closest one responds
    - from edge location, uses AWS backbone globally as needed
    - much better performance because less public internet involved
    - Can be used for NON HTTPS ( TCP/UDP) UNLIKE cloudfront