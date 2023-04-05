## General
    - peering is manual, not auto
    - operates over TCP/179 - it reliable
    - path-vector proptocol, exchanges best path only
    - uses shortest AS path as most preferred route
    - Can use AS Prepend to manipulate route tables

## bgp path selection
We Love Oranges AS Oranges Mean Pure Refreshment
    - Weight ( cisco propriety, default 0)
    - Local preference - advertised inside AS, default 100, HIGHEST preferred
    - Locally origiated - router will prefer routes which its the origin for
    - AS PATH length - SHORTEST preferreed
    - Origin Code 
    - MED - Multi Exit Discriminator preferred (from neighbor)
    - eBGP over iBGP 
    - shortest IGP path to next hop - LOWEST metric preferred
    - Oldest Path - stable...
    - Router ID - LOWEST ID
    - Loweset neighbor IP address

## Local Preference
    - Allows you to choose OUTBOUND paths
    - internal only (shared in only your AS, makes sense as outbound traffic only)
    - local pref WINS against ASPATH
    - default = 100

## MED ( Multi exit discrimainator)
    - influence path INBOUND
    - used if equal ASPATH 
    - LOWEST MED is preferred 
    - if you increase MED, it de-oprioritise the route
    - set it in site 1, site 2 RT will be updated with MED vaoue ( and thus pick correct route as wanted)
    - advertised to 'local' neighbors ONLY.

## AWS specific
    - reccomend use kcal pref to specific DX connection for OUTBOUND
    - use ASPATH prepending to get AWS to pref specific DX INBOUND
    - AWS sets an MED of 100 on VPN bgp sessions, meaning default of 0 of DX is preferred
    - TGW uses a diff ASN, so use ' bgp alwways-compare-med' on customer router.