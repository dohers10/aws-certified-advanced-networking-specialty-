## General
    - Origin; The source location of your content
            - S3 oriign or Custom origin
    - Distribution; the config of Cloudfront
    - Edge location; Local cache of your data
            - Small racks in 3rd party DC
            - 80% storage, 20% compute
            - Lots of them
    - Regional Edge Cache; Larger version of an edge location
            - Bigger than edge location
            - less of them
    - Integrateds wiht ACM/SSL
    - DOWNLOAD style only - no read &  WRITE caching

    - Origin <- Cache Behaviour <- distribution
    - Cache behaviour -
            - Can have many behaviours
            - eg. img/* go to diff S3 bucket
            - TTL, policies, private/public could be diff
    - Field Level Encrpytion - happens at the edge location

## TTL & Invalidations
    - More frequenet cahce hits ( origin fetches) = lower origin load
    - Default TTL = 24 hours (configured in behaviours). That is, 24 hours after file/image viewed, it is expired.
            -  Can set min and max TTL values.. this applies to any obkect that doesnt have below headers set.
    - Origin header : Cache-Control max-age (seconds)
            -> TTL value in seconds for an object, once passes its seen as expired. 
    - Origin header : Cache-Control s-maxage (seconds)
            -> SAME as above - TTL value in seconds for an object, once passes its seen as expired. 
    - Origin header : Expires ( Date and time)
            -> same as above but specific date and time
    - Custom origin or S# (object metadata - console, api etc)
    - Cache invalidation, done on distribution. Should only be done to fix errors
        -> Applies to all edge locations, take time
        -> Expires any objects ignoring TTL
        -> Cost involved
    - Versioned file names can do this without invalidation.
        -> Better to use
        -> change name means user cache not effected
        -> Logging better as specific to object
        -> Less expensieve, no cost.

## Cloudfront & SSL
    - SSL supported by default...  *.cloudfront.net cert
    - Alternate domain names ( CNAMES) for teh default distribution
            -> Needs a cert for this! Same name as your alt name distribution
    - Generate or import in ACM ( IN us-east-1 !!)
    - Can allow HTTP or HTTPS
    - Can redirect HTTP to HTTPS
    - Can ONLY allow HTTPS
    - 2 SSL conns ( BOTH of these need public certs - not self signed etc)
        -> viewer -> cloudfront
        -> cloudfront -> Origin
    - Supporting SSL on old browsers require dedicated IP -> ~ $600 per month for CF! This is becasue tehy dont support SNI

## OAI/OAC - Origin Access Identities/ Origin Access Control 
        - For restricting where access can come from
                - OAC the now reccomended option
                - OAI is attached to a resource such as Cloudfront

## Geerestriction
        - 2 types
                - Cloudfront Geo Restriction
                        - CF - Whitelist or Blacklist - COUNTRY only
                        - CF - GEOIP DB is 99.8% accurate, applied to entire distribution
                        - if country is not whitelisted or in blacklists - returns a 403 (forbidden) to user.
                                        - Can be custom error
                        
                - 3rd Party Geolocation
                        - Completly customasiable - can be MUCH more accurate! 
                        - Can be based on users, browsers etc
                        - 

## Private behaviours, Signed URL & Cookies
        - Private; requests require signed cookie or signed URL
                - 2 ways to make private
                        - OLD way -> cloudfront key
                        - NEW way -> Trusted Key group(s) added. 
        - Signed Urls - provide access to ONE oject ONLY
                - Use is client DOESNT support cookies
        - Cookies - Provides access to GROUPS of objects
                - To maintain application URL, use cookie.

# Lambada @ Edge
        - Can run lightweight lambda at edge locations
        - Adjust data between viewer & Oriign
        - only Node.js and Python
        - Can NOT access VPC ( runs in AWS public zone)
        - Use-cases;
                - Viewer request versions ( eg. change url based on anything)
                - Migrating between S3 origins
                - Different objects based on device ( eg. better devies better quality)
                - 