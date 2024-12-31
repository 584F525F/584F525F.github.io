!!! info ""

    ### Proxy ARP
	
    - Proxy ARP is needed in a 1:1 NAT configuration because it allows the router to respond to ARP requests for the public IP address on behalf of the private IP address.
	- When a host on the private network wants to communicate with a host on the public network, it sends an ARP request to find the MAC address associated with the public IP address. Without proxy ARP, the router would not be able to respond to this ARP request and the communication would fail.
	- By enabling proxy ARP on the router, it can respond to ARP requests for the public IP address on behalf of the private IP address, allowing communication to take place. This is necessary because the router needs to be able to forward the traffic between the private and public networks, and proxy ARP allows the router to function as a proxy for ARP requests for the public IP address.
	- In summary, the purpose of proxy ARP is to allow the router to respond to ARP requests on behalf of the private IP address and to allow communication between the private and public networks.

!!! info ""

    ### Configuration Template

    - CHECK THE ADDRESS BOOK CONFIGURATION FIRST AS SCRIPT MIGHT NEED AN UPDATE!
    - This is a Static 1:1 NAT configuration with security policy to allow access from a single specific Public IP Address to a Single Private Address on all Port (No port translation)

    **The following will need to be changed in the script**

    - **<FromX-ToY>** Enter rule name such as VendorToEquipmentX
    - **<RuleName>** Enter Rule Name for rule
    - **<public-ip-being-accessed/32>** The Public IP address that the client will access from Internet
    - **<destination-lan-IP/32>** The Private assigned IP for the client device
    - **<AddBookName-VendorEquipment>** Address Book name that will be created for the Vendor limited access
    - **<local-access-name>** address set name for local device
    - **<destination-lan-IP/32>** address of the device on lan
    - **<public-access-name>** address set name for vendor
    - **<source-public-accessing/32>** public ip src address that the vendor will use to access their equipment
    - **<Zonename-Vendor>** security policy zone name for the vendor

    ```bash    
    set security nat static rule-set <FromX-ToY> from zone Internet 
    set security nat static rule-set <FromX-ToY> rule <RuleName> match destination-address <public-ip-being-accessed/32>
    set security nat static rule-set <FromX-ToY> rule <RuleName> then static-nat prefix <destination-lan-IP/32>

    set security nat proxy-arp interface ge-0/0/0.0 address <public-ip-being-accessed/32>

    set security address-book <AddBookName-VendorEquipment> address <local-access-name> <destination-lan-IP/32>
    set security address-book <AddBookName-VendorEquipment> address <public-access-name> <source-public-accessing/32>

    set security policies from-zone <Zonename-Vendor> to-zone Internet policy permit-all match source-address <public-access-name> 
    set security policies from-zone <Zonename-Vendor> to-zone Internet policy permit-all match destination-address <local-access-name> 
    set security policies from-zone <Zonename-Vendor> to-zone Internet policy permit-all match application any 
    set security policies from-zone <Zonename-Vendor> to-zone Internet policy permit-all then permit 

    set security policies from-zone Internet to-zone <Zonename-Vendor> policy server-access match source-address <public-access-name> 
    set security policies from-zone Internet to-zone <Zonename-Vendor> policy server-access match destination-address <local-access-name>
    set security policies from-zone Internet to-zone <Zonename-Vendor> policy server-access match application any
    set security policies from-zone Internet to-zone <Zonename-Vendor> policy server-access then permit
    ```

!!! info ""

### Example

```bash
+-------------+     +-------------+
| Public      |     | Private     |
| Network     |---->| Network     |
|             |     |             |
| 5.5.5.5:9090|     |10.0.0.2:443 |
+-------------+     +-------------+

In above example
- a host on the public network is trying to access the private IP address 10.0.0.2 on port 443
- The 1:1 NAT rule, maps the public IP address 5.5.5.5 and port 9090 to the private IP address 10.0.0.2 and port 443.
- When the host on the public network sends a request to the public IP address 5.5.5.5 on port 9090, the router will forward the request to the private IP address 10.0.0.2 on port 443.
the source IP address is 5.5.5.5 and source port is 9090, the destination IP address is 10.0.0.2 and destination port is 443. The router is doing a 1:1 mapping of these IP addresses and ports so that the host
```

Example configuration

```bash
# Create a rule-set named "private-to-public" for the zone Internet 
set security nat static rule-set private-to-public from zone Internet 

# Create a rule named "web-server" that matches the destination address of the public IP being accessed
set security nat static rule-set private-to-public rule web-server match destination-address 5.5.5.5/32

# Apply the NAT action to the private IP addresses and use the public IP address 5.5.5.5 and map public port 9090 to private port 443
set security nat static rule-set private-to-public rule web-server then static-nat prefix 10.0.0.2/32 port 9090

# Enable proxy ARP for the public IP address 5.5.5.5 on the ge-0/0/0 interface
set security nat proxy-arp interface ge-0/0/0.0 address 5.5.5.5/32

# Create an address book named "access-list" and specify the private and public IP addresses
set security address-book global address access-list address local-access-name 10.0.0.2/32
set security address-book global address access-list address public-access-name 5.5.5.5/32

# Create a security policy to allow traffic from the Vendor zone to the Internet zone
set security policies from-zone Vendor to-zone Internet policy permit-all match source-address public-access-name 
set security policies from-zone Vendor to-zone Internet policy permit-all match destination-address local-access-name
set security policies from-zone Vendor to-zone Internet policy permit-all match application any
set security policies from-zone Vendor to-zone Internet policy permit-all then permit

# Create a security policy to allow traffic from the Internet zone to the Vendor zone
set security policies from-zone Internet to-zone Vendor policy server-access match source-address public-access-name 
set security policies from-zone Internet to-zone Vendor policy server-access match destination-address local-access-name
set security policies from-zone Internet to-zone Vendor policy server-access match application any
set security policies from-zone Internet to-zone Vendor policy server-access then permit
```
