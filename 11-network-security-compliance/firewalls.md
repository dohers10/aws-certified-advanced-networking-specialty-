## L7 Firewalls
    - L3/4 seperate flows for REQ and RESP
    - L5 - understands both, statful.
            - Neither of these know anythign above.
    - L7 is everythigbn below and above. Eg. HTTP
    - Understands session ID
    - Can identify normal AND abnormal reqs ( protocol specific attacks)
    - Data at L7 can be inspected, blocked, replaced or tagged.

## WAF
    - WEBACL
        - Default action - ALLOW or BLOCK
        - Resource tpye - Cloudfront ( GLOBAL) or regional service
            - ALB, API GW, Appysnc etc have to configure region
        - Need Rule groups/rules - processed in order
        - WCU ( Web ACL Capacity Units) - default 1500, can be increased.
            - indication of com,plexity of rules
        - Webacls assciated with resources
        - Resource can have 1 webacl, 1 webacl to many resources
    - Rulegroups
        - No default actions
        - Managed ( aws/Marketplace), yours or service owneed ( shield/Firewall manager)
        - Rule groups can be reffed by many WEBACLS
        - Have a WCU capacity ( defined upfront - max 1500)
    - Rules
        - Type, Statemnt, Action
            - Type: Regular or rate-based. Eg. something that occurs (src IP = X) vs something occurs at certain rate (SSH attempt > 5000 over 5 min period)
            - Statement : WHAT to match ( incoming SSH/HTTP rule header). 
                    - Examples - origin country, ip, label, header, cookies, URI path, query string, body ( FIRST 8192 bytes ONLY), http method
            - Action : Allow, Block , Count, Captcha, Custom response, Label (internal to WAF only - can be referenced)
                        - Allow/block hapens - stop processing
                        - Count/Captcha happens - keeps processing, where labels used)
