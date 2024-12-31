!!! info ""

    #### Summary
    
    IGMP (Internet Group Management Protocol) allows several devices to share one IP address so they can all receive the same data.

    Unicast/Multicast can be used in streaming videos or other services, functions on Layer 2 of the OSI Layer.

    ![alt text](/Knowledge_Base/images/igmp-09us.png)

!!! info ""

    #### IGMP devices

    - **IGMP device:** A switch or router running IGMP traffic control features.
    - **IGMP host:** An end-node device running an IGMP (multipoint or multicast communication) application.
    - **Querier:** 
        - A required IGMP device that facilitates IGMP protocol and traffic flow on a given LAN. This device tracks which ports are connected to devices (IGMP clients) that belong to specific multicast groups and triggers updates of this information.
        - A querier uses data received from the queries to determine whether to forward or block multicast traffic on specific ports.
        - When the switch has an IP address on a given VLAN, the switch automatically operates as a querier for that VLAN if it does not detect a multicast router or another switch functioning as a querier.
        - When enabled (the default state), the switch’s querier function eliminates the need for a multicast router. In most cases, HP recommends that you leave this parameter in the default enabled state even if you have a multicast router performing the querier function in your multicast group. For more information, see [How IGMP operates](https://techhub.hpe.com/eginfolib/networking/docs/switches/YA-YB/15-18/5998-8157_yayb_2530_atmg/content/ch03s04.html "How IGMP operates").


!!! info ""

    #### IGMP Basics

    IGMP used by a **Host** to notify the local **Router** that it wishes to receive (or stop receiving) multicast traffic for a given group address. Below diagram shows a basic multicast service model. IGMP’s functionality is shown in item 2.b in the diagram.

    ![alt text](/Knowledge_Base/images/igmp-1.png)

    There are 3 versions (IGMP v1, IGMP v2 & IGMP v3) available. The most common version of deployment is IGMP v2. Once you enable PIM on a layer 3 interface it will automatically enable IGMPv2 on that interface. If a host want to join for a particular multicast group, they will send a IGMP Membership report to 224.0.0.2 (all-routers in local subnet) & first  hop router will get it. When another host in the same network requesting same group, layer 2 switch will suppress that request. You can disable this feature by using “no ip igmp snooping report-suppression” command if needed.

    ![alt text](/Knowledge_Base/images/igmp-2.png)

    Normally (without IGMP snooping) a switch will forward a multicast frame to all switch ports (except incoming port). IGMP snooping allows the switch to send multicast frames only to those receivers that join a particular group by listening for report/leave messages from the hosts. By default this feature is enabled on a layer 2 switch. If you want to enable is only on particular VLAN you can disable it globally & configure “_ip igmp snooping vlan vlan-id_” with required vlan-id.

    When a client want to leave the group they will send a “IGMP Leave Msg” to 224.0.0.2 (&  first hop router will get it). Then router will query “IGMP Query Msg” to 224.0.0.1 (All-Host multicast address). As long as at least one client is in this group, switch will forward IGMP Membership report back to first hop router. In IGMP v2.0 you can configure fast-leaving feature by using “_ip igmp snooping vlan vlan-id immediate-leave_“. In this way switch will immediately remove the port from multicast forwarding table.

    ![alt text](/Knowledge_Base/images/igmp-3.png)

    If no users join for the multicast group, router will not get any response & it will wait for 3 x query interval to decide no users require this multicast stream any longer. Then it will pass that info to upstream routers to stop forwarding multicast traffic to that group.

    ![alt text](/Knowledge_Base/images/igmp-4.png)

    **Compare to IGMPv2, IGMPv3 has following advantages**

    1. Hosts can join one group and leave another in the same transaction. IGMPv2 requires separate report/leave messages.  
    2. Reduces the likelyhood of multicast group being spoofed by a rogue source.  
    3. Eliminates overlapping multicast addresses.  
    4. First-hop router immediately knows the source address, so no need for RP (Rendezvous Point) – can use PIM-SSM.

    Following shows IGMPv3 operation. In IGMPv3 all host membership reports send to 224.0.0.22 (IGMPv3 routers multicast address). There is no report-suppression in IGMPv3.

    ![alt text](/Knowledge_Base/images/igmp-5.png)

    ![alt text](/Knowledge_Base/images/igmp-6.png)


