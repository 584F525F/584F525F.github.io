It is recommended that AP Firmware version should be same as DP [Data lan] version. The same versions of AP(s) and DP(s) could ensure a onsistent agreement on functional communication.

!!! info ""

    #### General commands

    Those are commands I generally use to make certain checks

    ```bash
    show version

    show alarm

    #show resource usage
    show meminfo
    show diskinfo

    #usually after rebooting a SmartZone it takes a while to have all services running, thise can be seen more in multi node clusters.
    show service
    service start

    #check on the control plane
    show control-plane-stats SZ-Name type cpu period 8-h
    show control-plane-stats SZ-Name type memory period 8-h
    show control-plane-stats SZ-Name type disk period 8-h
    show control-plane-stats SZ-Name type port Port1 period 8-h
    show control-plane-stats SZ-Name type interface control period 8-h

    en
    diagnostics
    show snap (show previous snap shots)
    execute all (create new snap shot)
    ```

!!! info ""

    #### copying backup through FTP

    ```bash
    copy backup 
    copy backup-config 
    copy backup-network 

    upgrade ftp://ftpuser:ftpuser123@<IP Address>/FileName

    upgrade ftp://ftpuser:@10.10.10.52/scge-installer_5.2.0.0.699.ximg
    upgrade ftp://ftpuser:ftpuser123@10.10.10.52/scge-installer_6.1.0.0.935.ximg
    ```

!!! info ""

    #### check upgrade history & state

    Usually I run upgrades through GUI and I then check on progress through CLI, simply because I found CLI is more accurate and updated and didn't experience any issues while using it this way.

    ```bash
    show upgrade-history
    show upgrade-state
    ```

!!! info ""

    #### show backup & restore    

    ```bash
    show backup
    restore
    ```
