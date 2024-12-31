!!! info ""

    #### Sources

    [ARP RFC-826](https://datatracker.ietf.org/doc/html/rfc826)
    https://www.erg.abdn.ac.uk/users/gorry/course/inet-pages/arp.html


!!! info ""

    #### ARP

    ARP (Address Resolution Protocol)
    A way for devices to locate the Ethernet hardware address of another IP host on the same local network. Map IP network addresses to the hardware addresses used by a data link protocol.


!!! info ""

    #### Gratuitous ARP

    Gratuitous ARP is used when a node (end system) has selected an IP address and then wishes to defend its chosen address on the local area network (i.e. to check no other node is using the same IP address). It can also be used to force a common view of the node's IP address (e.g. after the IP address has changed).

    Use of this is common when an interface is first configured, as the node attempts to clear out any stale caches that might be present on other hosts. The node simply sends an arp request for itself.

!!! info ""

    #### Proxy ARP

    Proxy ARP is the name given when a node responds to an arp request on behalf of another node. This is commonly used to redirect traffic sent to one IP address to another system.

    Proxy ARP can also be used to subvert traffic away from the intended recipient. By responding instead of the intended recipient, a node can pretend to be a different node in a network, and therefore force traffic directed to the node to be redirected to itself. The node can then view the traffic (e.g. before forwarding this to the originally intended node) or could modify the traffic. Improper use of Proxy ARP is therefore a significant security vulnerability and some networks therefore implement systems to detect this. Gratuitous ARP can also help defend the correct IP to MAC bindings.

!!! info ""

    #### Types of arp messages

    There are four types of arp messages that may be sent by the arp protocol. These are identified by four values in the "operation" field of an arp message. The types of message are:

    - ARP-Request (Broadcast, source IP address of the requester)
    -ARP-Reply (Unicast to requester, the target)


!!! info ""


