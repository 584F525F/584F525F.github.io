You can use the command IP route or IP link to see the current network configuration and adapters in Linux. The program that manages the network configuration is typically the Network Manager or network service daemon, such as systemd-networkd or networkd-dispatcher. You can check which service is currently managing the network by running the command systemctl status NetworkManager or systemctl status **network daemon**

#### system os timed reboot
??? ""
    ```shell
    #IN 10 Minutes
    sudo shutdown -r +10

    #AT o'clock
    sudo shutdown –r 16:15
    #Cancel
    shutdown -c
    ```

#### restart network service
??? ""
    ```bash
    **TO RESTART - NEW WAY**
    sudo systemctl restart NetworkManager

    **TO RESTART - OLD WAY**
    sudo service network-manager restart
    ```

#### Checking network status
??? ""
    ```bash
    systemctl status network-manager

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

#### Network files location
??? ""
    ```bash
    nano /etc/NetworkManager/NetworkManager.conf
    nano /etc/network/interfaces
    ```

#### Using VLAN
??? ""
    ```bash
    #setting up VLANs
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

#### nmcli
??? "nmcli installation"
    ```bash
    sudo apt-get install -y network-manager
    ```

??? "show general status"
    ```bash
    nmcli general status
        
    STATE      CONNECTIVITY  WIFI-HW  WIFI     WWAN-HW  WWAN
    connected  full          enabled  enabled  enabled  enabled
    ```

??? "show device status"
    ```bash
    nmcli dev status

    DEVICE    TYPE      STATE      CONNECTION
    eth0      ethernet  connected  Wired connection 1
    VLAN1049  vlan      connected  vlan-VLAN1049
    lo        loopback  unmanaged  --
    ```

??? "show ip link"
    ```bash
    ip link show

    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 00:1e:06:48:b2:17 brd ff:ff:ff:ff:ff:ff
    3: VLAN1049@eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DEFAULT group default qlen 1000
    link/ether 00:1e:06:48:b2:17 brd ff:ff:ff:ff:ff:ff
    ```

??? "show nmcli connections"
    ```bash
    nmcli con
    #To show active only use switch -a    $ nmcli con -a>

    NAME                UUID                                  TYPE      DEVICE
    Wired connection 1  96a930f1-7119-3f77-a0e9-76356a82cceb  ethernet  eth0
    vlan-VLAN1049       c5e76778-76fc-49f9-bbb5-cff1a55e0704  vlan     VLAN1049
    ```

??? "nmcli modify connection"
    ```bash
    sudo nmcli con modify VLAN1049 802-3-ethernet.cloned-mac-address 00:1e:06:37:71:39
    ```

??? "nmcli add connection"
    ```bash
    sudo nmcli con add type vlan ifname VLAN1049 dev eth0 id 1049
    sudo nmcli con up VLAN1049
    sudo nmcli con up vlan-VLAN1049

    sudo nmcli con add type vlan ifname VLAN1000 dev eth0 id 1000
    sudo nmcli con up VLAN1000
    sudo nmcli con up vlan-VLAN1000

    You will see it in green instead of Orange once you run nmcli con show again
    ```

??? "nmcli Delete"
    ```bash
    #Get <NAME> field value
    nmcli connection show
    #Delete for <NAME>
    sudo nmcli connection delete id <NAME>
    ```

??? "Setting a dev as managed"
    ```bash
    sudo nmcli dev set vlan1049 managed yes
    ```


#### Route
??? ""
    ##### Show route
    ```bash
    route -n

    Kernel IP routing table    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         10.30.30.1      0.0.0.0         UG    0      0        0 eth0
    0.0.0.0         10.20.20.1      0.0.0.0         UG    300    0        0 eth0.1000
    10.5.0.0        10.10.10.1      0.0.0.0         UG    0      0        0 vlan1049
    ```

    ##### Route DELETE
    ```bash
    sudo route del -net 0.0.0.0 gw 10.30.30.1 netmask 0.0.0.0 dev eth0
    sudo route del -net 0.0.0.0 gw 10.20.20.1 netmask 0.0.0.0 dev eth0.1000
    sudo route del -net 0.0.0.0 gw 10.10.10.1 dev vlan1049
    ```

    ##### Route ADD
    ```bash
    sudo route add -net 0.0.0.0 gw 172.20.0.1 dev VLAN1049
    sudo route add -net 0.0.0.0 gw 172.20.0.1 dev VLAN1000
    sudo route add -net 0.0.0.0 gw 172.20.0.1 dev eth0.1000
    sudo route add -net 0.0.0.0 gw 172.20.0.1 dev eth0.1049
    ```

    ##### Check Route
    Keep in mind that you will loose access if the Route looks like this, you need to wait for your routes to fully populate, might take a bit so keep checking
    ```bash
    route -n

    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         10.155.115.254  0.0.0.0         UG    100    0        0 eth0
    0.0.0.0         172.20.0.1      0.0.0.0         UG    400    0        0 VLAN1049
    10.155.115.128  0.0.0.0         255.255.255.128 U     100    0        0 eth0
    169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 VLAN1049
    172.20.0.0      0.0.0.0         255.255.240.0   U     400    0        0 VLAN1049
    ```
    Table should look like this, if green is missing then if you delete the eth0 route, you can’t reach the device
    ```bash
    route -n

    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         10.155.115.254  0.0.0.0         UG    0      0        0 eth0
    0.0.0.0         10.155.115.254  0.0.0.0         UG    100    0        0 eth0
    0.0.0.0         172.20.0.1      0.0.0.0         UG    400    0        0 VLAN1049
    10.5.0.0        10.155.115.254  255.255.0.0     UG    0      0        0 eth0
    10.155.115.128  0.0.0.0         255.255.255.128 U     100    0        0 eth0
    64.128.110.192  10.155.115.254  255.255.255.240 UG    0      0        0 eth0
    66.192.125.32   10.155.115.254  255.255.255.224 UG    0      0        0 eth0
    66.195.172.208  10.155.115.254  255.255.255.240 UG    0      0        0 eth0
    72.45.133.192   10.155.115.254  255.255.255.224 UG    0      0        0 eth0
    169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 VLAN1049
    172.20.0.0      0.0.0.0         255.255.240.0   U     400    0        0 VLAN1049
    216.136.47.32   10.155.115.254  255.255.255.240 UG    0      0        0 eth0
    ```

    ##### Adding a WLAN Adapter
    ```bash
    Need to add a WLAN adapter? Have staff connect it to an open USB port on an ODROID
    Sudo ifconfig
    wlan0 Link encap:Ethernet HWaddr 40:a5:ef:f3:9a:17 UP BROADCAST MULTICAST MTU:1500 Metric:1 RX packets:0 errors:0 dropped:222 overruns:0 frame:0 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

    sudo iwconfig wlan0 essid "Hilton Honors"
    sudo dhclient wlan0
    sudo ifconfig wlan0 up
    ifconfig wlan0

    nmcli dev status
    nmcli radio wifi
    nmcli radio wifi on
    nmcli dev wifi list
    sudo nmcli dev wifi connect network-ssid
    sudo nmcli dev wifi connect network-ssid password "network-password"

    #Managing Network Connections With nmcli
    #You can view all the saved connections by issuing the following command:
    nmcli con show

    #If you're connected to one network, but want to use a different connection, you can disconnect by switching the connection to down. You'll need to specify the SSID, or if you have multiple connections with the same SSID, use the UUID.
    nmcli con down ssid/uuid

    #To connect to another saved connection, simply pass the up option in the nmcli command. Make sure that you specify the SSID or UUID of the new network that you want to connect to.
    nmcli con up ssid/uuid

    wlan0 Link encap:Ethernet HWaddr 40:a5:ef:f3:9a:17 inet addr:192.168.20.85 Bcast:192.168.23.255 Mask:255.255.252.0
    ```


### Netplan
- Resources
  - [https://tom-henderson.github.io/2019/04/12/ubuntu-vlan-config.html](https://tom-henderson.github.io/2019/04/12/ubuntu-vlan-config.html)
  - [https://netplan.io/examples](https://netplan.io/examples)

??? "netplan YAML"
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
                    vlan1049:
                        id: 1049
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
                    vlan1049:
                        id: 1049
                        link: eth0
                        addresses: [172.20.100.1/22]

    #To test the file run below
    sudo netplan generate <filename>.yaml

    ## To try the config file
    sudo netplan try <filename>.yaml

    #while in /etc/netplan/
    sudo netplan apply
    ```
