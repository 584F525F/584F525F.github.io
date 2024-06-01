!!! info ""

    ### How to deal with Broadcast Storms

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
    show int | i cast
    ```


!!! info ""

    ### Multicast (IGMP)

    #### Summary

    When a device processes a multicast packet, by default, it broadcasts the packets to all ports except the incoming port of a VLAN. Packets are flooded by hardware without going to the CPU. This behavior causes some clients to receive unwanted traffic.

    IGMP snooping provides multicast containment by forwarding traffic to only the ports that have IGMP receivers for a specific multicast group (destination address). A device maintains the IGMP group membership information by processing the IGMP reports and leave messages, so traffic can be forwarded to ports receiving IGMP reports. An IPv4 multicast address is a destination address in the range of 224.0.0.0 to 239.255.255.255. Addresses of 224.0.0.X are reserved.

    If a VLAN is not IGMP snooping-enabled, it floods multicast data and control packets to the entire VLAN in hardware. When snooping is enabled, IGMP packets are trapped to the CPU. Data packets are mirrored to the CPU in addition to being VLAN flooded. The CPU then installs hardware resources, so that subsequent data packets can be switched to desired ports in hardware without going to the CPU. If there is no client report or port to queriers for a data stream, the hardware resource drops it.

    ##### IGMP modes
    
    The default mode is passive. Below are the 2 IGMP modes

    - **Active**
      actively sends out IGMP queries to <mark>identify multicast groups on the network</mark>, and makes entries in the IGMP table based on the group membership reports it receives.
    - **Passive**
       it forwards reports to the router ports which receive queries. IGMP snooping in the passive mode does not send queries. However, it <mark>forwards queries to the entire VLAN</mark>.

    ##### The commands

    ```bash
    #To globally set the IGMP mode
    device(config)#ip multicast active

    #To set the IGMP mode for VLAN 20, enter the following commands.
    device(config)#vlan 20
    device(config-vlan-20)#multicast active

    #You can set the IGMP version this way, same syntax if IGMP over VLAN
    device(config)#ip multicast version 3
    Syntax: [no] ip multicast version [2 | 3]
    #If you do not specify a version number, IGMP V2 is assumed.

    #multicast reporting
    ip multicast report-control

    #displaying the IGMP snooping configuration
    sh ip multicast

    #display information about IGMP groups
    sh ip multicast group

    #displaying the status of IGMP snooping traffic
    sh ip multicast traffic

    #displaying a list of multicast groups
    sh ip pim group

    #displaying PIM mcache table entries
    sh ip pim mcache

    #disables flooding of unregistered IPv4 multicast frames in an IGMP-snooping-enabled VLAN
    ip multicast disable-flooding
    ```


    !!! info ""

        #### Multicast (pvlan)

        Primary VLANs. pvlan type command specifies that this port-based VLAN is a PVLAN and can be of the following types:

        - **community**: Broadcasts and unknown unicasts received on community ports are sent to the primary port and also are flooded to the other ports in the community VLAN.
        - **Primary**: Broadcasts and unknown unicasts received on Primary ports are sent only to the primary port. They are not flooded to other ports in the Primary VLAN.
        - **primary**: The primary PVLAN ports are "promiscuous". They can communicate with all the Primary PVLAN ports and community PVLAN ports in the Primary and community VLANs that are mapped to the promiscuous port.

        When setting pvlan type on VLAN you might get an error stating protected port

        ```bash
        (config-vlan-800)#pvlan type Primary
        Error: Protected ports can't be added to private vlans
        ```

        In case you got above error, you will need to disable protected port on any interfaces you have it set on, then you can set the type of isolation on the VLAN

        ```bash
        #example of removing protected-port from ports 1-14
        (config-mif-1/1/1-1/1/14)#no protected-port
        
        #navigate to your vlan, in this case we have vlan 800
        (config-mif-1/1/1-1/1/14)#vlan 800
        
        #before making the change, lets have a reference point to compare with
        (config-vlan-800)#show int | i cast

        #make the change to the pvlan type desired
        (config-vlan-800)#pvlan type Primary
        #You can ignore the below messages
        #Warning: Primary Port 1/1/1 is member of Regular VLANs 300  
        #Warning: Primary Port 1/1/2 is member of Regular VLANs 300  

        (config-vlan-800)#wr mem
        (config-vlan-800)#clear statistics

        #wait a few minutes and then see how many multicast you are seeing now, keep running the command every few minutes and it should have a stable increment value (nothing crazy)
        (config-vlan-800)#show int | i cast
        ```

        This should take care of multicast storm issues, of course you will need to issue `clear statistics` command after each change and monitor if the changes are actually working or not
        
        ![alt text](ICX-s98nsxz-0.png)

        After the change

        ![alt text](/Knowledge_Base/images/ICX-s98nsxz-1.png)
        
        You can also try Limiting multicast, but I do not recommend this.

        ```bash
        #limit multicast Pkts/sec
        multicast limit 10000
        ```


    !!! info ""

        #### Access Point Multicast disable

        If you're having IPTV issues while STB plugged into an Access Point port, you can disable the Multicast on the AP itself, this could solve the issue.

        ```bash
        #check qos configuration on a specific port
        get qos eth4

        #disabling the multicast per AP port, you will have to check how many ports your AP has
        set qos eth0 directed multicast disable
        set qos eth1 directed multicast disable
        set qos eth2 directed multicast disable
        set qos eth3 directed multicast disable
        set qos eth4 directed multicast disable
        ```

!!! info ""

    ### IPv4 ACLs

    IPv4 ACLs that filter based on VLAN membership or VE port membership
    (Router image only) You cannot change VLAN membership on a port while per-port-per-vlan is enabled

    ```bash
    #in global config run the below and then reload the switch
    enable acl-per-port-per-vlan
    wr mem
    exit
    reload

    #do this on all ports EXCEPT the UPLINK PORT
    int eth 1/1/x to 1/1/x
    loop-detection shutdown-disable

    int eth 1/1/x to 1/1/x
    source-guard enable
    wr mem
    ```

    OR

    Create an ACL and assign it

    ```bash
    ip access-list extended ACL
     permit ip 172.17.52.0 0.0.3.255 host 172.17.52.2
     deny ip 172.17.52.0 0.0.3.255 host 224.0.0.251
     deny udp 172.17.52.0 0.0.3.255 any eq 5353
     permit ip any any
    ```
