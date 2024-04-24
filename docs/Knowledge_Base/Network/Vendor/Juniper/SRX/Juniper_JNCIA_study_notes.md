!!! info ""

    ```bash
    RE  > routing, exception traffic, 
    PFE > does policies such as routing policies, Qos, filters
    PFE > transit traffic, unicast and multicast traffic
    ```

!!! info ""

    ### Navigating JunOS

    !!! success ""

        #### shortcuts

        Space bar is for word completion
        Tab is for word & user-defined variables completion 
        ctrl+k delete from cursor to end of line
        ctrl+w delete word to left

    !!! success ""

        #### help commands

        ```bash
        #Shows commands and help topic for them
        Help apropos

        #Show command full sytax, description and information
        Help reference

        #shows example of config for specific topic
        Help topic
        ```

    !!! success ""

        #### file system

        ```bash

        file list 
        save

        #primary boot (Compact Flash wd0 or Internal flash). Contains running config and last 3 commits
        /config

        #user home directory, ssh keys, path to save and load config ,,
        /var/home

        #config backups for rollback, upto 49
        /var/db/config

        #system log
        /var/log

        #core files
        /var/tmp
        ```

!!! info ""

    ### Interfaces & Basic config

    !!! success ""

        #### JUNOS Interfaces
        
        - **FXP0 me0** : for Management OOB
        - **FXP1 me0** : for Internal Management CP/FP
        - **interface sequence MM-F/P/T**
        - MediaType-ChassisSlotNumber/PICSlot/PortNumber
        - [example](https://www.juniper.net/documentation/us/en/hardware/mx480/topics/topic-map/mx480-interface-modules-dpcs.html)
        - **Physical Interface Card [PIC]**
        - **Flexible PIC Concentrator [FPC]**

    !!! success ""
    
        #### Network Interfaces
        - ethernet
        - sonet
        - etc..

    !!! success ""
    
        #### Service Interfaces
        - logical services
        - gre tunnel
        - ip tunnel
        - encryption
        - Loopback Interfaces

    !!! success ""

        #### Physical Interfaces speeds
        - xe > 10Gb
        - et > 40Gb
        
        **Interface Physical properties**
        - speed
        - duplex
        - MTU
        - Data Link layer Protocol
    
    !!! success ""

        #### Logical properties
        - Protocol Family (inet, inet6, ..)
        - Address (IPv4, IPv6)
        - VLANs

!!! success ""

        #### extra sources
        - [junos enterprise routing](https://www.oreilly.com/library/view/junos-enterprise-routing/9781449309633/ch04s01.html)
        - [router interfaces overview](https://www.juniper.net/documentation/us/en/software/junos/interfaces-fundamentals/topics/topic-map/router-interfaces-overview.html)

!!! success ""

        #### Commands

        ```bash
        traceoptions, syslog, snmp, ntp

        Config archival 
            set system archival configuration
            transfer-interval
            transfer-on-commit

        rename: move config from one interface to another
        load factory-default
        ```

!!! info ""

    ### Monitor, Upgrade & Recovery

    !!! success ""

        #### SW, HW 

        ```bash
        #verifies SW info/Statistics
        show system ....

        #verifies HW info/Statistics
        show chassis ...

        #shows temp
        show chassic environment

        #Monitor used for live monitoring
        Monitor interfaces ge000

        #firmware upgrade
        #Install a software package on all Routing Engines in a cluster
        #System Halt (Recomended before doing hardshutdown) vs shutdown (Turns off the CP but still device is on)
        #When upgrading software, must be placed in /var/tmp/
        #Software must match on all REs - UISU Unified In Service Upgrade

        request system software add 
        ```

    !!! success ""

        #### Routing & forwarding tables

        - **inet.0**
        ipv4 unicast routing table (stores interface local and direct routes, static routes, and dynamically learned routes)  

        - **inet6.0**
        ipv6 unicast routing table (stores interface local and direct routes, static routes, and dynamically learned routes)

        - **inet.1**
        IPv4 multicast forwarding cache (stores the IPv4 (S,G) group entries that are dynamically created as a result of join state information)      

        - **inet6.1**
        IPv6 multicast forwarding cache (stores interface local and direct routes, static routes, and dynamically learned routes)

        - **inet.3**
        IPv4 MPLS paths (stores the egress address of an MPLS label-swiched path (LSP), the LSP name, and the outgoing interface name)

        - **mpls.0**
        MPLS next hop

        - **inet.2**
        Used for URPF - prevent loops

        - **instance-name.inet.0**
        If you configure a routing instance, Junos OS creates the default unicast routing table instance-name.inet.0.

        - **instance-name.inet.2**
        If you configure routing-instances instance-name protocols bgp family inet multicast in a routing instance of type VRF, Junos OS creates the instance-name.inet.2 table.

        Forwarding table has exisiting interface and next adjacent IP address

    !!! success ""

        #### Routing Preferences

        ```bash
        0       Direct/Local
        5       Static 
        10      OSPF Internal
        15/18   ISIS Internal
        100     RIP
        150     OSPF External
        160/165 ISIS External
        170     BGP
        ```

    !!! success ""

        #### Routing Instances 

        Creates Internal Router, Virtually isolated Interfaces and has it's own Routing Table
        There is a Master Routing Instance and you can then create user-defined instances which is called Global Routing table

    !!! success ""

        ##### Types of routing instances

        - **Forwarding**
        Use this routing instance type for filter-based forwarding applications. no 1:1 mapping between Interface and Instance, all Interfaces belong to inet.0

        - **No-Forwarding**
        There is no corresponding forwarding table. All routes are installed into the default forwarding table. 

        - **L2VPN**            

        - **Virtual-Router**
        Similar to a VPN routing and forwarding instance type, but used for non-VPN-related applications. 

        - **VPLS**
        Use the virtual private local-area network service (VPLS) routing instance type for point-to-multipoint LAN implementations between a set of sites in a VPN. 

        - **VRF**
        Use the VPN routing and forwarding routing (VRF) instance type for Layer 3 VPN implementations. 1:1 mapping between instance and interface

        Junos OS routing protocol process (rpd) is responsible for synchronizing the routing information between the routing and forwarding tables. Only the active routes are installed in the forwarding table.
        The routing protocol process then copies the forwarding table to the routers Packet Forwarding Engine.
        RE has Routing Table & Master Forwarding Table 
        PFE has Forwarding Table

        [additional resource](https://www.dasblinkenlichten.com/understanding-the-junos-routing-table/)

    !!! success ""

        #### JUNOS Services

        - **rpd**: routing protocol process
        - **device control process (dcd)**: controls the devices interfaces
        - **management process (mgd)**: user access 
        - **chassis process (chassisd)**: controls the devices properties itself
        - **Packet Forwarding Engine process (pfed)**: controls the communication between PFE and RE

        **Notes:**
        - In static Routing when you have something like a loopback and you're pinging another loopback. Even if reachable, by default the source IP being used is the physical interface IP adress and not the loop back or originating IP address
        - To get a response you must have the other path enabed to reach back to you
        If you ping and don't get a response that might be because you have a route to destination and no route back to the source
        - In Dynamic Routing when looking at routing table results, if you find a result then it should be %100 reachable as it's checked. Unlike Static Route where it might be not reachable

        
        Routing no-advertise is used to stop static ip redistribution into dynamic routing - This is configured in static route
        
        ```bash
        Default route is 0.0.0.0/0
        ```

        static route resolve is used when you have more than 2 routers, instead of defining the routes all the way, you set resolve and it figures it out through the in between Routers

        next-hop has default preference of 5
        qualified next-hop has a configurable preference

    ### Routing Policies & Options

    - Routing Policies & Options > Acts on Routing Information
    - Routing Policies applied to Import & Export Policies
    - Routing Policy Match [If Route coming From?]  > conditions based upon a route's properties, prefix, route list, protocol, protocol attributes, next-hop, neighbors
    - Routing Flow Control Actions [Then? Action] : accept, default-action accept, reject, default-action reject, next term, next policy
    - Routing Policy Action Modifiers: local-preference, metric, next-hop, origin, preference
    - Will evaluate next term if first term not matching and does not require mention of next term

    !!! success ""

        **extra sources**:
        - [policy default actions default policies](https://www.juniper.net/documentation/us/en/software/junos/routing-policy/topics/concept/policy-default-actions-default-policies.html)
        - [juniper routing policy](https://codingpackets.com/blog/juniper-routing-policy/)
        - [Configuring Junos Policies Filters](https://disnetern.ru/wp-content/uploads/2016/11/DO_Configuring_Junos_Policies_Filters.pdf)

    It is possible, and highly probable, to have more than one match condition per term, There can be only a single terminating action, but the action statement can be used to modify several attributes of a prefix at the same time.

    Policy must match all items in a Term for it to be applied

    ```bash
    Prefix-Lists & Route Filters:
        Prefix-List: list of IPs, range, ..
            Prefix-List-Filter: exact, longer, orlonger, upto, prefix-length-range, through
        Route-filter: Exact IP or Range however it's not shared and only in the line you're using
            route-filter x.x.x.x/x address-mask x.x.x.x
    ```

    Policy evaluated and if no match, continue to next Policy, and If no match then default policy will be evaluated
    Policy evaluation will stop once a terminating action is found
    If a term does no contain a terminating action the next-term is evaluated.

    ``` bash
    policy-options {
        policy-statement POLICY-NAME {
            term {
                    from {
                        MATCH-CONDITIONS;
                        MATCH-CONDITIONS;
                        MATCH-CONDITIONS;
                    }
                    then {
                        ACTIONS;
                    }
            }
        }
    }

    term 1 {
        from {
            protocol bgp;
            rib vrf-customer2.inet.0;
            community customer;
        }
        then {
            next-hop next-table vrf-customer1.inet.0;
        }
    }
    ```

    You can specify next term and next policy to evaluate them as well
    In the Import - From > They must all be True in a term in order to run that term
    Matching with a prefix-list (Must match at least one of the entries) or prefix-list-filter (exact, longer, etc...)

    ```bash
    set protocols rip group to-R2 export advertise-routes-through-rip
    set policy-options policy-statement advertise-routes-through-rip term 1 from protocol direct
    set policy-options policy-statement advertise-routes-through-rip term 1 from protocol rip
    set policy-options policy-statement advertise-routes-through-rip term 1 then accept

    protocols {
        ospf {
            area 0.0.0.0 {
                interface ge-0/0/0.0;
            }
            export po;
        }
    }
    ```

    ### Routing Policies & Options Flow

    !!! success ""

        **Notes:**
        
        - Firewall Filters ACLs > Acts on Packets
        - Match conditions based on a packet matching different fields in packet header, Match source/destination, Match criteria includes port numbers, IP, etc..
        - Matching depends on each Family and it's properties, like family inet
        Route might be hidden because of an invalid next-hop or reject routing policy
        - Default action to Firewall Filter is discard

    !!! success ""

        **Firewall Policy**
        - **Firewall Policy Match condition**: check packet header for binary > src/dst address L3, src/dst port L4, protocol, bits
        - **Firewall Filter Terminating Actions**: accept, discard, reject
        - **Firewall Filter Action Modifiers**: count, log, syslog, policer, forwarding-class & loss-priority
        - **Firewall Filter Flow Control Action**: Next-term only
        When firewall filter matches a term and no action is set then default action is implicit accept and filter evaluation terminates

        ```bash
        firewall {
            family FAMILY-NAME {
                filter FILTER-NAME {
                    accounting-profile name; 
                    instance-shared;
                    interface-specific; 
                    physical-interface-filter; 
                    term term-name {
                        filter filter-name; 
                    }
                    term TERM-NAME {
                        from {
                            MATCH-CONDITIONS; 
                            ip-version ip-version { 
                                match-conditions;
                                protocol (tcp | udp) {
                                    match conditions; 
                                }
                            }
                        }
                        then {
                            ACTIONS,
                        }
                    }
                }
            }
        }
        ```

        Applying above to inet family on a ge port. This will apply the filter on outgoing packets.

        ```bash
        root# show interfaces
        ge-0/0/0 {
            unit 0 {
                family inet {
                    filter {
                        output TEST;
                    }
                    address 10.10.10.1/24;
                }
            }
        }
        ```
    
    !!! success ""
        additional source: [firewall filter stateless guidelines for configuring](https://www.juniper.net/documentation/us/en/software/junos/routing-policy/topics/concept/firewall-filter-stateless-guidelines-for-configuring.html)

    !!! success ""

        #### Firewall Filters ACLs

        !!! info ""
            ##### Unicast RPF (URPF)

            **Unicast Reverse Path Forwarding**:
            - If I know how to reach you then you are excepted otherwise, discarded Usually configured on edge devices.
            - This is an antispoofing/DOS checking mechanism.
            - This controls the routers installed in the RE.

            **URPF Modes**:

            - Strict Mode: 
                - It has to be able to reach it back on the same Interface it was reached. if Juni gets packet on ge-0/0/0 then it has to be able to reach back that address form this Interface.
                - Routing Table must have a route installed that can lead back to the Source address and the next-hop for that route.
                - Asymmetric Routing is not allowed.

            - Lose Mode: 
                - It will allow reaching back to the source address through a different Interface.
                - Any route installed in the RE can be used to reach back to the Source. But it it required to have some oute than can accomplish that.
                - Asymmetric Routing is allowed

        !!! info ""
            
            **requirement to have devices communicate on IP network**
            - end to end communications path
            - routing information on participating L3 devices

        !!! info ""

            RE handels protocol processes, SW processes that control chassis, interfaces, system management & user access. Also controls PFE by providing L2 & L3 forwarding tables 

            ```bash
            Default import/export policy
            BGP    Imports-All    Exports-All
            OSPF   Imports-All    Exports-None*
            IS-IS  Imports-All    Exports-None*
            RIP    Imports-All**  Exports-None

            *Flooding will happen by default for IntraArea routes only
            **Imports only from manually configured neighbors
            ```

            ```bash
            show route output
            ```
        
        !!! info ""

            **Permissions**
            - **operator**: Clear, network, reset, trace, and view permissions;
            - **read-only**: View permissions; and
            - **unauthorized**: No permissions.
