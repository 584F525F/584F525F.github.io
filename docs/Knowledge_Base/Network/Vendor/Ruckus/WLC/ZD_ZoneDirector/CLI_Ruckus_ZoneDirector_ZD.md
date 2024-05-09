!!! info ""

    #### ZD AP Firmware Compatability to Join ZD

    ZD firmware version 9.13.x or lower > AP with Standalone Firmware 100.x is supported.
    ZD firmware version 10.x or later   > AP with Standalone Firmware 104.x or above is supported.


    #### Firmware upgrade

    ```shell
    enable
    config
    system
    ftp
    ftp-anon
    
    show sysinfo

    debug
    save config X.X.X.X backup

    fw_upgrade -p ftp -s 10.121.147.129 -n zd1200_10.1.2.0.318.ap_10.1.2.0.318.img 
    ```

    fw_upgrade options

    ```shell
    fw_upgrade
                Upgrade the controller’s firmware
                protocol
                Protocol for image transfer (FTP, TFTP, HTTP, KERMIT)
                OPTIONS
                    -p	protocol
                    -s	server IP address or name
                    -n	image name with path on the server
                    -f	non-verbose mode
                    -h  fw_upgrade help message
    ```

!!! info ""

    #### FTP

    Type in the following commands to enable and disable the FTP as well as FTP anonymous.

    ```shell
    en    
    config
    system
    ```

    ##### Enable ftp

    ```shell
    ruckus(config-sys)# ftp
    ```

    ##### Disable ftp

    ```shell
    ruckus(config-sys)# no ftp
    The FTP access has been disabled.
    ```

    ##### Enable ftp login anonymous

    ```shell
    ruckus(config-sys)# ftp-anon
    The FTP anonymous access has been enabled.
    ```

    ##### Disable ftp login anonymous

    ```shell
    ruckus(config-sys)# no ftp-anon
    The FTP anonymous access has been disabled.
    ```

    Please make sure that you enable ftp in case you need to upgrade the firmware anytime. Anonymous FTP can stay disabled for ZD/AP upgrade.

!!! info ""

    #### Enable LLDP

    ```shell
    enable
    config
    ap-group "xxxx"
    lldp enable
    exit
    exit
    ```

!!! info ""

    #### Renaming APs

    ```shell
    enable
    config
    ap xx:xx:xx:xx:xx
    location xxxxx
    devname xxxx
    exit
    exit
    ```
