!!! info ""


    ```bash
    conf t
    int eth 1/1/x to 1/1/x
    loop-detection
    spanning-tree
    stp-bpdu-guard
    stp-protect

    #limit multicast Pkts/sec
    multicast limit 10000

    clear statistics
    wr mem


    show loop-detection status
    show span
    show stp-bpdu-guard
    show stp-protect-ports
    show statistics
    show int eth 1/1/1 | i cast
    ```

    IPv4 ACLs that filter based on VLAN membership or VE port membership
    (Router image only) You cannot change VLAN membership on a port while per-port-per-vlan is enabled

    ```bash
    #in global config run the below and then reload the switch
    enable acl-per-port-per-vlan
    wr mem
    exit
    reload

    int eth 1/1/x to 1/1/x
    source-guard enable
    wr mem
    ```
