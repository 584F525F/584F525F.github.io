!!! info ""

    #### Step 1: Configure forwarding options

    To do this, navigate to forwarding-options and then to packet-capture hierarchy as below:
    
    ```bash
    [edit]
    edit forwarding-options packet-capture

    #Specify a file name for the packet capture and set the maximum-capture-size to 1500 as below
    set file filename packetcapture
    set maximum-capture-size 1500

    show
        file filename testpacketcapture;
        maximum-capture-size 1500;

    top
    ```

!!! info ""

    #### Step 2: Configure firewall filter for packet capture

    This is strongly recommended because with the firewall filter, the amount of traffic to be capture can be restricted, and it is less CPU intensive, as compared without filters.

    To do this, set the filter, term name, define the match condition, and its action.

    **For example** the firewall filter below will collect traffic that arrives on the interface with a source address of 10.209.242.138 AND destination-address of 10.204.115.166 AND vice versa. The term allow-all-else is used to make sure that the SRX does not drop any other traffic, but do not sample it either.

    ```bash
    set firewall filter PCAP term 1 from source-address <public_ip>
    set firewall filter PCAP term 1 then sample
    set firewall filter PCAP term 1 then accept
    set firewall filter PCAP term 2 from destination-address <public_ip>
    set firewall filter PCAP term 2 then sample
    set firewall filter PCAP term 2 then accept
    set firewall filter PCAP term allow-all-else then accept
    ```

!!! info ""

    #### Step 3: Apply firewall filter to desired interface

    Decide which interface you want to capture the packets on. This must be an Ethernet interface.
    
    For this example, interface ge-0/0/0 is used. Apply the firewall filter on the desired interface for the input and output direction:

    **FOR VLAN TAGGING**

    ```bash
    set interfaces ge-0/0/0 unit 0 family inet filter output PCAP
    set interfaces ge-0/0/0 unit 0 family inet filter input PCAP
    ```
    
    **FOR ethernet-switching**

    ```bash
    set interfaces ge-0/0/0 unit 0 family ethernet-switching filter output PCAP
    set interfaces ge-0/0/0 unit 0 family ethernet-switching filter input PCAP
    ```
    
!!! info ""

    #### Step 4: Commit to activate the packet capture

    ```bash
    user@host# commit
    ```

    Once you commit, then run your test to pass the traffic that needs to be captured.
    Once the test is complete, deactivate the packet capture to stop the collection of packets. To do this, remove the packet-capture and sampling configuration that was just added above and commit. A quick way to do this is using rollback:

    ```bash
    user@host# rollback 1
    user@host# commit
    ```
 
!!! info ""

    #### Step 5: Copy packet capture file from the SRX device, and view it with your PCAP utility

    The captured file is located in the /var/tmp directory and is formatted in the PCAP format. You can find the file with the file list command.

    ```bash
    user@host> file list /var/tmp/ | match testpacketcapture*  
    testpacketcapture1.ge-0.0
    ```
    Copy this file to your PC.

    The packet capture file created can be viewed with Wireshark, Ether


    SAMPLE FOR CAPTURE

    ```bash
    edit forwarding-options packet-capture
    set file filename AWSVPN-Capture
    set maximum-capture-size 1500
    show
    top

    set firewall filter PCAP term 1 from destination-address <public_ip>
    set firewall filter PCAP term 1 then sample
    set firewall filter PCAP term 1 then accept
    set firewall filter PCAP term allow-all-else then accept
    
    set interfaces ge-0/0/0 unit 0 family inet filter output PCAP
    set interfaces ge-0/0/0 unit 0 family inet filter input PCAP
    
    commit

    rollback 1
    commit

    ```

!!! info ""

    Sources: [How to create a PCAP packet capture on a SRX branch device](https://supportportal.juniper.net/s/article/Includes-video-How-to-create-a-PCAP-packet-capture-on-a-SRX-branch-device?language=en_US)
