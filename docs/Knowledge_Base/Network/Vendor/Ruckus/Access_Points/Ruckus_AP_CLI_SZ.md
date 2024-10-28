!!! info ""

    #### execute AP CLI commands remotely from SCG

    ```bash
    remote ap-cli <AP-MAC-Address> “AP CLI command”
    ```

    #### display SCG Settings

    ```bash
    get scg
    ```

    #### set the IP Address of the control interface

    ```bash
    set scg ip “IP Address”
    ```

    #### show ZoneDirector information

    ```bash
    get director
    ```

    #### set ZoneDirector IP

    Reboot is required for changes to take effect

    ```bash
    set director ip “IP Address”
    ```

    #### ping another station

    ```bash
    ping
    ```

    #### traceroute test

    ```bash
    traceroute
    ```

    #### display the software version running on the AP

    ```bash
    get version
    ```

    #### display how long the Ruckus Wireless device has been running.

    ```bash
    get uptime
    ```

    #### get CPU and memory utilization information

    ```bash
    sysinfo
    ```

    #### display AP operation mode (standalone or managed mode)

    ```bash
    get ap-mode
    ```

    #### display hardware version and system board information

    ```bash
    get boarddata
    ```

    #### generate support log information

    ```bash
    support
    ```

    #### show support log information

    ```bash
    support show
    ```

    #### show all to display firmware

    ```bash
    fw show all
    ```

    #### display tunnelmgr settings

    ```bash
    get tunnelmgr
    ```

    #### display all WLAN interfaces

    If the AP is a dual radio AP, the RadioID column indicates which radio (2.4GHz or 5GHz) is serving the WLAN.

    ```bash
    get wlanlist
    ```

    #### list all configured wlan interfaces and security settings

    ```bash
    get wlaninfo
    ```

    #### display the transmit channel on the device

    ```bash
    get channel <wlan name>
    ```

    #### display the state of a WLAN interface

    ```bash
    get state <wlan name>
    ```

    #### configure the state of a WLAN interface

    ```bash
    set state <wlan name> {up|down}
    ```

    #### get station list, information and statistics

    ```bash
    get station <wlan name> list
    ```

    #### display Media Queue Statistics

    ```bash
    get mqstats <wlan name> all
    ```

    #### display AP certificate information

    ```bash
    get rpki-cert {issuer|subject|validity}
    ```

    #### restart the AP

    ```bash
    reboot
    ```

    #### return all configuration settings to their factory defaults

    ```bash
    set factory
    ```

    #### Remote packet with Wireshark

    ```bash
    #This sets up packet capture on 2.4GHz radio
    set capture wlan100 stream
    
    #This displays status of 2.4GHz radio capture
    get capture wlan100 state
    
    #To stop the capture on 2.4GHz radio
    set capture wlan100 idle
    
    #This sets up packet capture on 5GHz radio
    set capture wlan101 stream
    
    #This displays status of 5GHz radio capture
    get capture wlan101 state
    
    #To stop the capture on 5GHz radio
    set capture wlan101 idle
    
    ```
