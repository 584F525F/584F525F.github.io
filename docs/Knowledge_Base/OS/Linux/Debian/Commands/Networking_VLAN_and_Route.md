!!! info ""

    #### system os timed reboot

    ```shell
    #IN 10 Minutes
    sudo shutdown -r +10

    #AT o'clock
    sudo shutdown –r 16:15

    #Cancel
    shutdown -c
    ```


!!! info ""

    #### restart network service

    TO RESTART - NEW WAY

    ```bash
    sudo systemctl restart NetworkManager
    ```

    TO RESTART - OLD WAY

    ```bash
    sudo service network-manager restart
    ```


!!! info ""

    #### Checking network status

    ```bash
    systemctl status network-manager
    ```

    result example

    ```bash
    NetworkManager.service - Network Manager
    Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
    Active: active (running) since Sat 2022-12-31 14:04:46 UTC; 16h ago
    Docs: man:NetworkManager(8)
    Main PID: 3102 (NetworkManager)
    Tasks: 3 (limit: 3831)
    Memory: 12.9M
    CGroup: /system.slice/NetworkManager.service
    └─3102 /usr/sbin/NetworkManager --no-daemon
    ```


!!! info ""

    #### Network configuration files locations

    ```bash
    sudo nano /etc/NetworkManager/NetworkManager.conf
    sudo nano /etc/network/interfaces
    ```

!!! info ""

    #### Using VLAN

    setting up VLANs

    ```bash
    sudo apt install -y vlan
    modprobe 8021q

    **if VLANx**
    sudo ifconfig up VLANx
    sudo dhclient VLANx

    **if eth0.x**
    #sudo vconfig add eth0 x
    sudo ifconfig up eth0.x
    sudo dhclient eth0.x
    ```

!!! info ""

    #### nmcli

    ##### nmcli installation

    ```bash
    sudo apt-get install -y network-manager
    ```

    ##### show general status

    ```bash
    nmcli general status
        
    STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN
    connected  full          enabled  enabled  enabled  enabled
    ```

    ##### show device status

    ```bash
    nmcli dev status

    DEVICE    TYPE      STATE      CONNECTION
    eth0      ethernet  connected  Wired connection 1
    VLAN50  vlan      connected  vlan-VLAN50
    lo        loopback  unmanaged  --
    ```

    ##### show ip link

    ```bash
    ip link show
    ```

    ```bash
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 00:11:22:48:b2:17 brd ff:ff:ff:ff:ff:ff
    3: VLAN50@eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether 00:11:22:48:b2:17 brd ff:ff:ff:ff:ff:ff
    ```
    ##### Adding a WLAN Adapter

    Need to add a WLAN adapter? Connect it to an open USB port on the device

    ```bash
    Sudo ifconfig
    wlan0 Link encap:Ethernet HWaddr 05:06:07:f3:9a:17 UP BROADCAST MULTICAST MTU:1500 Metric:1 RX packets:0 errors:0 dropped:222 overruns:0 frame:0 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

    sudo iwconfig wlan0 essid "WLAN_NAME"
    sudo dhclient wlan0
    sudo ifconfig wlan0 up
    ifconfig wlan0

    nmcli dev status
    nmcli radio wifi
    nmcli radio wifi on
    nmcli dev wifi list
    sudo nmcli dev wifi connect network-ssid
    sudo nmcli dev wifi connect network-ssid password "network-password"
    ```

    ##### using different connections

    If you're connected to one network, but want to use a different connection, you can disconnect by switching the connection to down. You'll need to specify the SSID, or if you have multiple connections with the same SSID, use the UUID.

    ```bash
    nmcli con down ssid/uuid
    ```

    To connect to another saved connection, simply pass the up option in the nmcli command. Make sure that you specify the SSID or UUID of the new network that you want to connect to.

    ```bash
    nmcli con up ssid/uuid

    wlan0 Link encap:Ethernet HWaddr 05:06:07:f3:9a:17 inet addr:192.168.20.85 Bcast:192.168.23.255 Mask:255.255.252.0
    ```

    ##### show nmcli connections

    ```bash
    nmcli con show
    #To show active only use switch -a    $ nmcli con -a>
    ```

    example

    ```bash
    NAME                UUID                                  TYPE      DEVICE
    Wired connection 1  96a930f1-7119-3f77-a0e9-76356a82cceb  ethernet  eth0
    vlan-VLAN50       c5e76778-76fc-49f9-bbb5-cff1a55e0704  vlan     VLAN50
    ```

    ##### nmcli modify connection

    ```bash
    sudo nmcli con modify VLAN50 802-3-ethernet.cloned-mac-address 00:11:22:37:71:39
    ```

    ##### nmcli add connection

    ```bash
    sudo nmcli con add type vlan ifname VLAN50 dev eth0 id 50
    sudo nmcli con up VLAN50
    sudo nmcli con up vlan-VLAN50

    sudo nmcli con add type vlan ifname VLAN200 dev eth0 id 1000
    sudo nmcli con up VLAN200
    sudo nmcli con up vlan-VLAN200

    You will see it in green instead of Orange once you run nmcli con show again
    ```

    ##### nmcli Delete

    ```bash
    #Get <NAME> field value
    nmcli connection show
    #Delete for <NAME>
    sudo nmcli connection delete id <NAME>
    ```

    ##### Setting a dev as managed

    ```bash
    sudo nmcli dev set vlan50 managed yes
    ```

!!! info ""
    
    #### Route
    
    ##### Show route

    ```bash
    route -n

    Kernel IP routing table    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         10.30.30.1      0.0.0.0         UG    0      0        0 eth0
    0.0.0.0         10.20.20.1      0.0.0.0         UG    300    0        0 eth0.35
    10.5.0.0        10.10.10.1      0.0.0.0         UG    0      0        0 vlan50
    ```

    ##### Route DELETE

    ```bash
    sudo route del -net 0.0.0.0 gw 10.30.30.1 netmask 0.0.0.0 dev eth0
    sudo route del -net 0.0.0.0 gw 10.20.20.1 netmask 0.0.0.0 dev eth0.35
    sudo route del -net 0.0.0.0 gw 10.10.10.1 dev vlan50
    ```

    ##### Route ADD

    dev syntax depends on how you have those devices set up. You can check by using 'nmcli conn show'

    ```bash
    sudo route add -net 0.0.0.0 gw 172.20.0.1 dev VLAN50
    sudo route add -net 0.0.0.0 gw 172.20.0.1 dev eth0.50
    ```

    ##### Check Route

    Keep in mind that you will loose access if the Route looks like this, you need to wait for your routes to fully populate, might take a bit so keep checking

    ```bash
    route -n

    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         10.20.20.254  0.0.0.0         UG    100    0        0 eth0
    0.0.0.0         172.20.0.1      0.0.0.0         UG    400    0        0 VLAN50
    10.20.20.128  0.0.0.0         255.255.255.128 U     100    0        0 eth0
    169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 VLAN50
    172.20.0.0      0.0.0.0         255.255.240.0   U     400    0        0 VLAN50
    ```

    Table should look like this. If you want to delete the eth0 default route so you can force all traffic on a VLAN, you will lose connectivity to the device.
    In most cases you can regain access if you bounce the Switch port the device is connected to (Disable > wait a few seconds > Enable).

    ```bash
    route -n

    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         10.50.115.20  0.0.0.0         UG    0      0        0 eth0
    0.0.0.0         10.50.115.20  0.0.0.0         UG    100    0        0 eth0
    0.0.0.0         172.20.0.1      0.0.0.0         UG    400    0        0 VLAN50
    10.20.20.0        10.50.115.20  255.255.0.0     UG    0      0        0 eth0
    10.50.20.128  0.0.0.0         255.255.255.128 U     100    0        0 eth0
    20.128.20.192  10.50.115.20  255.255.255.240 UG    0      0        0 eth0
    66.20.20.32   10.50.115.20  255.255.255.224 UG    0      0        0 eth0
    20.195.20.20  10.50.115.20  255.255.255.240 UG    0      0        0 eth0
    20.45.20.192   10.50.115.20  255.255.255.224 UG    0      0        0 eth0
    169.20.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 VLAN50
    172.20.0.0      0.0.0.0         255.255.240.0   U     400    0        0 VLAN50
    20.20.47.32   10.50.115.20  255.255.255.240 UG    0      0        0 eth0
    ```

!!! info ""

    ### Netplan

    - Resources
    - [https://tom-henderson.github.io/2019/04/12/ubuntu-vlan-config.html](https://tom-henderson.github.io/2019/04/12/ubuntu-vlan-config.html)
    - [https://netplan.io/examples](https://netplan.io/examples)

    ```YAML
    sudo apt update
    sudo apt install [netplan.io](<http://netplan.io/>)
    reboot
            
    cd /etc/netplan/
    sudo nano 01-netplan-config.yaml
            
    network:
        renderer: networkd
            ethernets:
                eth0:
                dhcp4: true
                vlans:
                    vlan50:
                        id: 50
                        link: eth0
                        addresses: [172.20.100.1/22]
            
    network:
        ethernets:
            eth0:
                dhcp4: false
                addresses:
                    - 10.10.10.2/24
                gateway4: 10.10.10.1
                nameservers:
                    search: [mydomain, otherdomain]
                    addresses: [10.10.10.1, 1.1.1.1]
                vlans:
                    vlan50:
                        id: 50
                        link: eth0
                        addresses: [172.20.100.1/22]

    #To test the file run below
    sudo netplan generate <filename>.yaml

    #To try the config file
    sudo netplan try <filename>.yaml

    #while in /etc/netplan/
    sudo netplan apply
    ```

!!! info ""

    ### extra commands

    ```bash
    cat /proc/net/route
    ip route
    ip route get x.x.x.x
    ip route show table local
    #policy-based routing
    ip rule show
    ```
