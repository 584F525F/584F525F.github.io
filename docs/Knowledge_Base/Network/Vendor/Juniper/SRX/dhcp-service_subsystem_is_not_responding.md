I had an issue where it was reported that all recent client devices connecting to the WLAN are not getting an IP Address, I was able to see that on the WLAN Controller end (this was an Aruba Mobility Controller). I then needed to see what device on the network is providing DHCP, it was our Juniper SRX Firewall. Below are some of the checks I completed to determine what the issue was and to resolve it.

!!! failure "dhcp-service subsystem is not responding"


    ```bash
    show dhcp server binding summary
    ```

    ![juni-srx-dhcp-subsystem-not-responding](/Knowledge_Base/images/juni-srx-dhcp-subsystem-not-responding.png)

    ```bash
    show arp no-resolve | match irb.1234 | count
    ```

    ```bash
    show configuration | compare rollback ?
    ```

    ```bash
    Possible completions:
    0                    2023-10-30 16:59:23 EDT by userx via cli
    1                    2023-10-30 16:54:52 EDT by userx via cli
    2                    2023-10-26 17:26:49 EDT by usery via cli
    3                    2023-10-26 17:26:05 EDT by usery via cli commit confirmed, rollback in 5mins
    4                    2023-06-20 14:56:35 EDT by userd via cli
    5                    2023-06-20 14:56:01 EDT by userd via cli
    ```

    ```bash
    show configuration | no-more | display set | match 172.50.
    ```

    ```bash
    set access address-assignment pool x1 family inet network 172.50.0.0/16
    ```


    ```bash
    show arp no-resolve | match irb.1234 | count
    ```
    
    ```bash
    Count: 129 lines
    ```

    ```bash
    show arp no-resolve | match 0c:89:86:d2:1e:3e
    ```

    ```bash
    show dhcp server binding brief
    ```

    ```bash
    error: the dhcp-service subsystem is not responding to management requests
    ```
    
    ```bash
    restart dhcp-service
    ```

    ![juni-srx-dhcp-subsystem-not-responding-restart](/Knowledge_Base/images/juni-srx-dhcp-subsystem-not-responding-restart.png)

    ```bash
    Junos Dynamic Host Configuration Protocol process started, pid 80252
    ```

    ```bash
    show dhcp server binding
    ```

    ```bash
    IP address        Session Id  Hardware address   Expires     State      Interface
    172.50.0.122      113         00:52:5a:20:2e:a9  28800       BOUND      irb.1234
    172.50.2.85       596         00:50:5a:20:2e:85  28798       BOUND      irb.1234
    172.50.206.157    119590      00:50:5a:20:2e:9b  28798       BOUND      irb.1234
    172.50.1.75       325         00:50:5a:20:2e:a9  28795       BOUND      irb.1234
    172.50.2.199      710         00:50:5a:21:2e:03  28796       BOUND      irb.1234
    172.50.2.84       595         00:50:5a:21:2e:3c  28795       BOUND      irb.1234
    172.50.0.123      114         00:50:5a:25:2e:75  2324        BOUND      irb.1234
    172.50.2.90       601         00:50:5a:25:2e:95  3602        BOUND      irb.1234
    172.50.2.192      703         00:50:5a:25:2e:39  28798       BOUND      irb.1234
    172.50.151.250    39333       00:50:5a:25:2e:59  28798       BOUND      irb.1234
    172.50.151.153    39235       00:50:5a:26:2e:0a  28797       BOUND      irb.1234
    172.50.103.95     158946      00:50:5a:db:2e:cb  4208        BOUND      irb.1234
    172.50.58.75      159006      00:50:5a:1d:2e:ee  9902        BOUND      irb.1234
    172.50.103.57     158908      02:50:5a:26:2e:19  11479       BOUND      irb.1234
    172.50.103.130    158981      02:50:5a:20:2e:24  6981        BOUND      irb.1234
    172.50.103.62     158913      02:50:5a:9c:2e:8e  3380        BOUND      irb.1234
    172.50.101.242    158579      02:50:5a:7d:2e:fc  10641       BOUND      irb.1234
    172.50.69.96      84222       04:50:5a:14:2e:18  5061        BOUND      irb.1234
    172.50.102.199    158794      06:50:5a:2e:2e:05  6409        BOUND      irb.1234
    172.50.104.78     159186      06:50:5a:10:2e:0f  10997       BOUND      irb.1234
    172.50.98.203     157769      06:50:5a:87:2e:12  10478       BOUND      irb.1234
    172.50.101.205    158542      06:50:5a:80:2e:b3  9842        BOUND      irb.1234
    172.50.103.248    159100      0a:50:5a:3d:2e:4b  8707        BOUND      irb.1234
    172.50.102.130    158723      0a:50:5a:d3:2e:dd  7852        BOUND      irb.1234
    172.50.102.81     158674      0a:50:5a:50:2e:33  11358       BOUND      irb.1234
    172.50.104.92     159200      0c:50:5a:ab:2e:56  11436       BOUND      irb.1234
    172.50.103.45     158896      0e:50:5a:d3:2e:91  3300        BOUND      irb.1234
    172.50.101.87     158422      0e:50:5a:22:2e:c1  9821        BOUND      irb.1234
    172.50.102.220    158815      0e:50:5a:2e:2e:e1  7713        BOUND      irb.1234
    172.50.102.158    158752      10:50:5a:41:2e:34  8363        BOUND      irb.1234
    ```

