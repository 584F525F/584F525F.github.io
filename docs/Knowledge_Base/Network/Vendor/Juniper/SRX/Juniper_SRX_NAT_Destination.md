!!! info ""

    Destination NAT, The destination address of a packet is changed as it enters a router. This is often used to redirect incoming public Internet traffic to a specific internal host or network. For example, a public IP address of 1.1.1.1 is configured with a destination NAT rule to redirect incoming HTTP traffic to a web server located on the internal network at IP address 10.0.0.2.

    !!! warn ""    
        Replace RemoteDevice Private IP **<Private_IP>** Example: 172.20.105.10
        Replace with RemoteDevice WAN Public IP **<Public_IP/32>** Example: 60.32.32.32/32
        Replace both **<Natted_ZONE>** and **<Internet_ZONE>**
        Replace the Ports both **address port** and **destination-port**

    Below are example of multiple Destination NATs (HTTPS, SNMP & SSH)

    ```bash
    set security nat destination rule-set RemoteDevice_Port_Forwards from zone <Internet_ZONE>

    #HTTPS 8443 > 443
    set security nat destination pool RemoteDevice_HTTPS address <Private_IP>
    set security nat destination pool RemoteDevice_HTTPS address port 443
    set security nat destination rule-set RemoteDevice_Port_Forwards rule RemoteDevice_HTTPS match destination-address <Public_IP/32>
    set security nat destination rule-set RemoteDevice_Port_Forwards rule RemoteDevice_HTTPS match destination-port 8443
    set security nat destination rule-set RemoteDevice_Port_Forwards rule RemoteDevice_HTTPS then destination-nat pool RemoteDevice_HTTPS

    #SNMP 1610 > 1610
    #Configure RemoteDevice SNMP to be on port 1610
    set security nat destination pool RemoteDevice_SNMP address <Private_IP>
    set security nat destination pool RemoteDevice_SNMP address port 1610
    set security nat destination rule-set RemoteDevice_Port_Forwards rule RemoteDevice_SNMP match destination-address <Public_IP/32>
    set security nat destination rule-set RemoteDevice_Port_Forwards rule RemoteDevice_SNMP match destination-port 1610
    set security nat destination rule-set RemoteDevice_Port_Forwards rule RemoteDevice_SNMP then destination-nat pool RemoteDevice_SNMP

    #SSH 2202 > 22
    set security nat destination pool RemoteDevice_SSH address <Private_IP>
    set security nat destination pool RemoteDevice_SSH address port 22
    set security nat destination rule-set RemoteDevice_Port_Forwards rule RemoteDevice_SSH match destination-address <Public_IP/32>
    set security nat destination rule-set RemoteDevice_Port_Forwards rule RemoteDevice_SSH match destination-port 2202
    set security nat destination rule-set RemoteDevice_Port_Forwards rule RemoteDevice_SSH then destination-nat pool RemoteDevice_SSH

    #Check the security Zone and make sure you have system-services any-service configured
    set security zones security-zone <ZONE> interfaces ge-0/0/2.0 host-inbound-traffic system-services any-service

    #Check which Zone you need to configure - show security zones
    set security policies from-zone <Natted_ZONE> to-zone <Internet_ZONE> policy permit-all match source-address any
    set security policies from-zone <Natted_ZONE> to-zone <Internet_ZONE> policy permit-all match destination-address any
    set security policies from-zone <Natted_ZONE> to-zone <Internet_ZONE> policy permit-all match application any 
    set security policies from-zone <Natted_ZONE> to-zone <Internet_ZONE> policy permit-all then permit 

    #Check which Zone you need to configure - show security zones
    set security policies from-zone <Internet_ZONE> to-zone <Natted_ZONE> policy server-access match source-address any
    set security policies from-zone <Internet_ZONE> to-zone <Natted_ZONE> policy server-access match destination-address any
    set security policies from-zone <Internet_ZONE> to-zone <Natted_ZONE> policy server-access match application any
    set security policies from-zone <Internet_ZONE> to-zone <Natted_ZONE> policy server-access then permit

    ```
