# Fibre

Sindlemode (LX) - uses laser optics, long distance, small core. 
Multimode (OM) - Faster, shorter distances. Uses multiple modes ( rays) of light. 

SFP - Single Form factor pluggable. 
AWS DX supports 1000BASE-LX, 10GBASE-LR, 100GBASE-LR4.

## DDOS
App layer attacks - eg. HTTP floods (eg. ton of web requests)
Protocol Attack - eg. SYN floods ( Eg. spoof IP addresses, consume network resources for TCP handshake)
Columetric - eg. DNS amplification (eg. overhwlem DNS requests)

## SSL & TLS
- Privacy/Data integrity between client & server
- Starts with Asymmetric encryption, then symmetric. 
- Provides identity verification (is netflix.com legit)
    3 main phases ( layer4);
        1) Cipher Suites    - Client Hello ( ssl/tls versions, suppoerted cipher suites, session ID etc)
                            - Server Hello ( ssl/tls versions, chooses cipoher suite, server cert + public key to encrypt)
        2) Authentication   - As long as client trusts the CA, makes sure against CA that vert is valid/dns matches etc.
                            - Client then verifies the server has private key ( sends some data encrpytted)
        3) Key exchange     - Move from asymmetric to symmetric encrpytion ( better computationaly)


![TLS Architecture](images/SSLandTLS.png)