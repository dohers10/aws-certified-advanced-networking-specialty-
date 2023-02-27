## General
    - internet facing LB - can talk internal and external IPs.
    - 8 or more free IPs into a subnmett ( /27 reccomended) 
    - interneal LBs sed to seperate app tiers.
    - ELB is a DNS A record pointing at 1+ nodes per AZ
    - EC2 doesnt need to be public to work with a LB !


## ALB  
    - L7 LB.. Listens on HTTP/HTTPs - NOT SMTP/SSH/Gaming etc... NO TCOP/EDUP/TLS listeners
    - can do stuff with L7 contenet ( cookies, custom headers, user location etc)
    - HTTP/HTTPS ALWAYS terminated on the ALB.. Cannot have an unbroken SSL connection... New connection then to application on backend. eg. CANNOT do end to end encryption
    - MUST have SSL sert on ALB if https used
    - Slower than NLB as more layers to process
    - Evaulate application health ( L7)
    - Can use rules ( processed in priority order) - things like host headers, http headers, path-patterns/src ip etc then do something with this traffic
            - Action s- Forward, redirect, fixed http response ( error code etc)


## NLB
    - TCP, TLS, UDP, TCP_UDP
    - no visibility of HTTP/HTTPS
    - no headers/cookies, session stickiness etc
    - Fast! Great for performance
    - health check only ICMP/TCP handsjake
    - Can have static IPs - useful for whitelisting
    - can fwd TCP to instances ( unbroken encryption)
    - used for privatelink to provide services to VPCs

## ALB vs NLB examples
    - Unrboken encrpytion ... NLB
    - Static IP for whitelisting.,... NLB
    - BEST performance/low latency.... NLB
    - Protocols NOT http/https... NLB
    - privaleink... NLB
    - otherwise.... ALB

## Connection draining 
    - Classic LB only
    - allows in flight requests to complete, then no new connections
    - timeout value bertween 1 and 3600 ( default 300)

## Deregistration Delay
    - supported on ALB, NLB, GWLB
    - defined on TG NOT LB
    - existing conns contionue./complete naturally
    - ENABLED by DEFAULT
    - default is 200 secondsw ( 0 - 3600)

## X-Forwarded-for
    - Set of http headers
    - header is aded by proxies/LBs 
    - backend WEB server NEEDs to be aware of this
    - conns still from LB to server but contain original client IP
    - NLB NOT supported.. only CLB/ALB

## Proxy Protocol
    - works at L4
    - Addition L4 TCP header 
    - V1 CLB - V2 for NLB

## Security Policies
    - Set of cipgers/Prtocs configured on a listener
    - ensure secure comms client -<> server
    - cipher = alogritham - Ley + plaintext = ciphertext