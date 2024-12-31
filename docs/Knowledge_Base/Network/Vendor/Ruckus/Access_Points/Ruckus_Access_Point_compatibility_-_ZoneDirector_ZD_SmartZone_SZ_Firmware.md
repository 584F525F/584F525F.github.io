!!! info ""

    ** AP Firmware compatibility to Join ZD **

    ZD firmware version 9.13.x or lower > AP with Standalone Firmware 100.x is supported.
    ZD firmware version 10.x or later   > AP with Standalone Firmware 104.x or above is supported.

    AP utilizes SSH to communicate with the controller

    - APs running Solo 110.X and above
    - APs running SZ 5.x and above
    - APs running Unleashed 200.x and newer
        
    AP utilizes `LWAPP` to communicate with the controller

    - APs running ZD 9.x
    - APs running solo 104.x or prior

    ++++++++++

    In SmartZone under `Cluster Information` > Only first time config you can enable the AP Conversion (This enables `LWAPP`) > if not enabled then, you can re-enable it from GUI, you have to go to CLI
    You can enable this option or disable it through CLI when onboarding APs depending on compatibility

    ```bash
    >enable
    >Show run lwapp2scg
    ```
    
    check the policy if deny all or allow all

    ```bash
    #config
    #lwapp2scg
    #policy accept-all          >  choose this depending on what you need 
    #policy deny-all            >  choose this depending on what you need
    #end
    ```

    It is similar for vSZ/SZ, so for SZ/vSZ lower than 3.6.x, the AP standalone firmware 100.x is supported and for the firmware version higher than 5.x, the AP firmware version 104.x or higher is supported.


    IP mode on dual mode
    AP solo 114 latest .6565 and avoid .1360
    will have issue 5.1 or 5.2 SZ
    So you need to have only IPv4

    Latest APs should be on 114 but older try either 104 or 110 solo Firmware version

    on AP having issue with run `get syslog log`

    ```bash
    #set Controller IP
    set scg ip
    ```

    ping controller also if needed to check if you can reach it out

    Controller upgrade then you need to upgrade the APs
