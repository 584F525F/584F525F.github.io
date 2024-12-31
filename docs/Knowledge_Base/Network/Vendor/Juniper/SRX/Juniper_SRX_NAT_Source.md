!!! info ""

Source NAT: The source address of a packet is changed as it exits a router and enters a public network. This allows a private IP address to be translated to a public IP address. For example, a private network with the IP address range of 10.0.0.0/24 wants to access the internet. A router with a public IP address of 1.1.1.1 is configured with a source NAT rule that translates the source IP address of 10.0.0.0/24 to 1.1.1.1 as the packets leave the private network and enter the public network.


**Source NAT Configuration Template & Example**
    
    ```
    +-------------+     +-------------+
    | Public      |     | Private     |
    | Network     |<----| Network     |
    |             |     |             |
    | 5.5.5.5     |     |10.0.0.2     |
    +-------------+     +-------------+
    ```
    
    In this example, a host on the private network is trying to access a host on the public network using its private IP address 10.0.0.2. The source NAT rule, maps the private IP address 10.0.0.2 to the public IP address 5.5.5.5 When the host on the private network sends a request to the public network, the router will change the source IP address from 10.0.0.2 to 5.5.5.5 before forwarding the packet to the public network. This way, the public network will see the request coming from the public IP address 5.5.5.5 instead of the private IP address 10.0.0.2
    
    In this representation, the source IP address is 10.0.0.2 and the destination IP address is any IP address on the public network. The router is doing a 1:1 mapping of the source IP address 10.0.0.2 to the public IP address 5.5.5.5 so that the host on the private network can communicate with the host on the public network.
    
    The below configuration is for a router with a public IP address of 1.1.1.1 and a private network on ge-0/0/0 interface with IP address range of 10.0.0.0/24. It creates a pool of public IP addresses (1.1.1.2 to 1.1.1.254) that will be used for the NAT and matches the private IP addresses that need to be NATed. Then it applies the NAT action to the private IP addresses using the public IP pool and applies the NAT rule to the ge-0/0/0 interface.
    
    ```bash
    # Set up the interface that will be used for the NAT
    set interfaces ge-0/0/0 unit 0 family inet address 1.1.1.1/24
    
    # Create a pool of public IP addresses that will be used for NAT
    set security nat source pool public-ip address 1.1.1.2/32 to 1.1.1.254/32
    
    # Create a rule that will match the private IP addresses that need to be NATed
    set security nat source rule private-to-public match source-address 10.0.0.0/24
    
    # Apply the NAT action to the private IP addresses and use the public IP pool
    set security nat source rule private-to-public then source-nat pool public-ip
    
    # Apply the NAT rule to the interface that is connected to the private network
    set security nat source rule private-to-public then interface ge-0/0/0.0
    ```
