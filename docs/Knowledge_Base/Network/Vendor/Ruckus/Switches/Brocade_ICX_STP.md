!!! info ""


    ```bash
    conf t
    int eth 1/1/x to 1/1/x
    loop-detection
    spanning-tree
    stp-bpdu-guard
    stp-protect


    clear statistics
    wr mem

    show loop-detection status
    show span
    show stp-bpdu-guard
    show stp-protect-ports
    show statistics
    show int eth 1/1/1 | i cast
    ```

!!! info ""

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

!!! info ""

    Limiting multicast

    ```bash
    #limit multicast Pkts/sec
    multicast limit 10000
    ```


    Isolated VLAN. pvlan type command specifies that this port-based VLAN is a PVLAN and can be of the following types:

    - **community**: Broadcasts and unknown unicasts received on community ports are sent to the primary port and also are flooded to the other ports in the community VLAN.
    - **isolated**: Broadcasts and unknown unicasts received on isolated ports are sent only to the primary port. They are not flooded to other ports in the isolated VLAN.
    - **primary**: The primary PVLAN ports are "promiscuous". They can communicate with all the isolated PVLAN ports and community PVLAN ports in the isolated and community VLANs that are mapped to the promiscuous port.

    ```bash
    device(config)# vlan 800
    device(config-vlan-800)# untagged ethernet 1/1/1 to 1/1/14
    device(config-vlan-800)# pvlan type isolated
    ```

    When setting pvlan type on VLAN you might get an error stating protected port

    ```bash
    (config-vlan-800)#pvlan type isolated
    Error: Protected ports can't be added to private vlans
    ```

    You will need to disable protected port on any interfaces you have it set on then set the type of isolation on the VLAN

    ```bash
    (config-mif-1/1/1-1/1/14)#no protected-port

    (config-vlan-800)#pvlan type isolated
    #Warning: Isolated Port 1/1/1 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/2 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/3 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/4 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/5 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/6 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/7 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/8 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/9 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/10 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/11 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/12 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/13 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/14 is member of Regular VLANs 300  
    #Warning: Isolated Port 1/1/48 is member of Regular VLANs 300   
    #Warning: Isolated Port 1/2/1 is member of Regular VLANs 300  
    ```

    This should take care of multicast storm issues, of course you will need to issue `clear statistics` command after each change and monitor if the changes are actually working or not
    
    ![alt text](image.png)

    After the change

    ![alt text](image-1.png)

