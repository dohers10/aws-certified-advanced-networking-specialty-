## Flow Logs
    - Captures metadata only, not contents. (eg. IP src/dst etc)
        - at VPC level ( all ENIs in vpc)
        - Subnet - All ENIs in that subnet
        - ENIs directly.
    - NOT realtime - cannot rely on this to be realtime
    - S3, Cloudwatch as DST
    - Can use Athena to query S3 and only pay for amount of data read. 
    - Can chose ACCEPTED, REJECTED or ALL
    - Doesnt capture AWS Meta data server, Amazon DNS and Amazon windows license.

## Traffic mirroring
    - ENI is source
    - Targets are specific ENIs, NLBs or GWLBEs.
    - Filter used - direction, action, prot, SRS/dst port/ip
    - Session = SRC + Target + Filter ( Uses Vxlan)
    - UDP 4789 for Vxlan ( needs to be allows in SGs or listeners on NLBs)
    - ENIs can be src or target but not BOTH.
    - Flow logs do not capture traffic mirroring
    - Uses RTs
