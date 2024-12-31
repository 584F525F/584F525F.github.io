!!! info ""

    #### extra sources

    - [How to troubleshoot Problem Scenarios in VPN tunnels](https://kb.juniper.net/InfoCenter/index?page=content&id=KB10100&actp=METADATA)
    - [Juniper SRX & J Series Site-to-Site VPN Configuration Generator](https://support.juniper.net/support/tools/vpnconfig/#vpnSettings)
    - [YT - How to Troubleshoot IPSEC VPN (Phase 1) on a Juniper Networks SRX Firewall](https://www.youtube.com/watch?v=3Wi5apzhRcI&list=PLVuH5P0woWt2-IHDdRsBpRyQcmgNJxbng&index=4)

!!! info ""

    #### Check inactive tunnels first

    ```bash
    show security ipsec inactive-tunnels
    show security ike security-associations
    show security ipsec security-associations
    show security ipsec statistics
    ```

!!! info ""

    #### To restart SRX VPN
    
    ```bash
    clear security ike security-associations
    clear security ipsec security-associations
    restart ipsec-key-management

    #check IKE Phase 1 & 2
    show security ike
    run show security ike security-associations

    #set capture file name
    set security ike traceoptions file debug-ike.log

    #set the flag that you want to capture
    set security ike traceoption flag ike

    #save changes
    commit
    
    #check error reason > this doesn't get extensive detail though
    run monitor start debug-ike.log

    #Capture to check the reason > Check the proposal values, look for type & value
    monitor traffic interface ge-0/0/0 matching "port 500" extensive
    ```

    encryption types

    ```bash
    ene value=3des	-> Encryption 3DES
    ene value=ldes	-> Encryption DES
    ene value=0007 keylen value=0080 -> Encryption aes-128-cbc 
    ene value=0007 keylen value=00c0 -> Encryption aes-192-cbc
    ene value=0007 keylen value=0100 -> Encryption aes-256-cbc
    group dese value=modp768  -> DH Group 1
    group dese value=modpl024 -> DH Group 2 
    group desc value=0005 -> DH Group 5 
    group desc value=000e -> DH Group 14
    group desc value=0018 -> DH Group 24
    hash value=md5 -> Authentication type md5
    hash value=shal -> Authentication type shal
    hash value=0004 -> Authentication type sha-256
    hash value=0005 -> Authentication type sha-384
    (type-1ifeduration 1en-4 va1ue-0000c350)
    Convert HEX(c3500) TO Decimal (50000)
    ```

!!! info ""

    #### Enable tracing

    ```bash
    root# set security ike traceoptions ?
    Possible completions:
    + apply-groups         Groups from which to inherit configuration data
    + apply-groups-except  Don't inherit configuration data from these groups
    > file                 Trace file information
    > flag                 Tracing parameters for IKE
    no-remote-trace      Disable remote tracing
    
    {primary:node0}[edit]
    roott# set security ike traceoptions flag all  

    roott# set security ipsec traceoptions flag ?
    Possible completions:
    all                  Trace with all flags enabled
    next-hop-tunnel-binding  Trace next-hop tunnel binding events
    packet-drops         Trace packet drops
    packet-processing    Trace data packet processing events
    security-associations  Trace security association management events
    {primary:node0}[edit]
    roott# set security ipsec traceoptions flag all

    #To show the log
    show log <filename>
    ```
