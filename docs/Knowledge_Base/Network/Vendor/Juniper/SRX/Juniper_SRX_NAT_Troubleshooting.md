
!!! info ""
    
    ### Source & Destination NAT Troubleshooting
    
    ```bash
    #display information about the source NAT rules, including the number of packets and        ytes    that have been translated, as well as the number of active sessions
    show security nat source rule
    
    #display information about the destination NAT rules, including the number of packets     and       ytes that have been translated, as well as the number of active sessions
    show security nat destination rule
    
    #display information about the source NAT pools, including the number of addresses in     use       nd available
    show security nat source pool
    
    #display information about the destination NAT pools, including the number of addresses         n    use and available
    show security nat destination pool
    
    #shows all the statistics of all the NAT rules, including the number of packets and     bytes       hat have been translated, as well as the number of active sessions
    show security nat source rule all statistics
    
    #shows all the statistics of all the NAT rules, including the number of packets and     bytes       hat have been translated, as well as the number of active sessions
    show security nat destination rule all statistics
    
    #display information about the active flow sessions, including the source and     destination       ddresses and ports, as well as the NAT translation information
    show security flow session
    
    #It's important to note that the security flow session table is populated only when the         ession is created and 
    #the traffic matches a security rule that has the session-initiation flag set  
    show security flow session rule-name <NAT rule name>
    show security flow session source-address <source IP address>
    show security flow session destination-address <destination IP address>
    
    #shows the sessions that match the specified source NAT rule
    show security flow session source-nat-rule name
    
    #shows the sessions that match the specified destination NAT rule
    show security flow session destination-nat-rule name
    
    #allows you to trace the path of a packet from the source to the destination, including         he    NAT translations. It can help you to verify if the packets are reaching the       orrect    destination and if the NAT translations are being applied correctly
    traceroute
    traceroute 5.5.5.5 source 10.0.0.1
    ```

!!! info ""

    ### 1:1 NAT Troubleshooting

    ```bash
    #display the configured NAT rule-sets, including the name, from-zone, and to-zone of each       ule. It also shows the number of hits for each rule, which can be used to determine if     he    rule is being used
    show security nat rule-set
    
    #display the destination NAT rules and their statistics, including the number of packets        nd bytes that have been translated by each rule
    show security nat destination rule-set
    
    #display the source NAT rules and their statistics, including the number of packets and     ytes that have been translated by each rule
    show security nat source rule-set
    
    #display the proxy ARP entries, including the interface, IP address, and number of ARP      equests that have been handled by each entry
    show security nat proxy-arp

    #show configuration
    show security nat proxy-arp

    #You can also check the proxy arp for a specific interface
    show security nat proxy-arp interface <interface name>

    		>The output will show the interface name, the IP address that the proxy arp is configured for, and the number of ARP requests that have been handled by the proxy arp
    		>If the proxy arp is working as expected, you should see a non-zero value for the number of ARP requests
    
    		>It's important to note that proxy ARP is typically used in conjunction with NAT, so if the NAT is not working as expected, it's likely that the proxy ARP is not working as expected either
    		>It's also important to check if the proxy arp is enabled on the correct interfaces and that the interfaces are in the correct zone
    
    		>It's also good practice to check the arp table to confirm that the arp entries are being resolved correctly
    		>You can use the command show arp to check the arp table

    #display the security policies and their statistics, including the number of packets and        ytes that have been permitted or denied by each policy
    show security policies

    #show security policies
    show security policies

    #To check security policies for a specific source IP address
    show security policies source-address <source IP address>

    #To check security policies for a specific destination IP address
    show security policies destination-address <destination IP address>

    #To check security policies for a specific application
    show security policies application <application name>

    #display the routing table, which can be used to verify that the router is forwarding       raffic to the correct next-hop
    show route
    #To check the routing table for a specific source IP address
    show route <source IP address>

    #To check the routing table for a specific soudestination IP address
    show route <destination IP address> <source IP address>

    #To check the routing table for a specific Interface
    show route interface <interface name>

    #can be used to test connectivity from the router to a specific IP address, which can be        sed to verify reachability to the public or private IP addresses being accessed through     he NAT rule
    ping
    
    #can be used to trace the path of a packet from the router to a specific IP address,    hich    can be used to identify any issues with the routing path
    traceroute

    #look for nat
    show log messages | match nat
    
    #look for rule set name
    show log messages | match web-server
    
    #can be used to enable debugging for NAT, which can provide detailed information about  he    NAT process and any issues that may be occurring
    debug security nat
    ```

!!! info ""

    ### General commands

    ```bash
    #Debug with word nat
    debug security nat

    #Debug using rule set name
    debug security nat rule-set

    #Debug off
    no debug security nat
    ```

