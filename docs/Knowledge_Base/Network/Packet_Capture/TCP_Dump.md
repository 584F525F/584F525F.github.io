!!! info ""

    ### TCPdump Install

    For remote captures using tcpdump and without the use of sudo

    ```bash
    sudo mkdir /usr/sbin/tcpdump/
    sudo apt-get install tcpdump -y
    sudo groupadd pcap
    sudo usermod -a -G pcap $USER
    sudo chgrp pcap /usr/sbin/tcpdump
    sudo chmod 750 /usr/sbin/tcpdump
    sudo setcap cap_net_raw,cap_net_admin=eip /usr/sbin/tcpdump
    ```

    ### TCPdump Remote Capture

    Listener device on your switch should have a SPAN port (Port Mirroring) for your specific VLANs or Ports that you want to capture the traffic for

    Below example will capture traffic on VLAN 50 and write the output to cap.pcap located on Desktop and will filter ports 80,443,1812,1813 or host IP Address 192.168.1.50

    ```bash
    sudo tcpdump -U -s 756 -i eth0.50 -w ~/Desktop/cap.pcap 'port 80 or port 443 or port 1812 or port 1813 or host 192.168.1.50'
    ```
