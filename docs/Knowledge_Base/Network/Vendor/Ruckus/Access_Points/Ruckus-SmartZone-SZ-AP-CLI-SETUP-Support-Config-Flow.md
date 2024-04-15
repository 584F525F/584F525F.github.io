!!! info ""

    #### WAP WLC Communication method

    AP utilizes **SSH** to communicate with the controller
    - APs running Solo 110.X and above
    - APs running SZ 5.x and above
    - APs running Unleashed 200.x and newer
        
    AP utilizes **LWAPP** to communicate with the controller
    - APs running ZD 9.x
    - APs running solo 104.x or prior

    ##### LWAPP

    In SmartZone under Cluster Information > Only first time config you can enable the AP Conversion (This enables LWAPP) > if not enabled then, you can re-enable it from GUI, you have to go to CLI. You can enable this option or disable it through CLI when onboarding APs depending on compatabiliy

    ```bash
    enable
    Show run lwapp2scg
    #check the policy if deny all or allow all

    config
    lwapp2scg
    
    #from the below choose either accept-all to enable, or deny-all to disable
    policy accept-all
    policy deny-all
    
    end
    ```

    ##### SSH

    ```bash
    get ssh
    get sshtunnel
    get tunnelmgr
    ```

!!! info ""

    #### AP CLI based on platform support

    ```bash

    #works for uneashed
    enable
    ap-modeccess to all commands

    #works for uneashed  3.6+ 9.13+  110.x+   |   display SZ info
    get scg
    set scg enable

    #works for uneashed  3.6+ 9.13+  110.x+
    set scg ip [xxxxx]

    #works for uneashed  3.6+ 9.13+  110.x+   |   To delete the SZ IP
    set scg ip del

    #works for 3.6+ 9.13+  110.x+
    set factory

    #works for uneashed
    set-factory

    #Work for all
    reboot
    ```

!!! info ""

    #### Configuring AP models to join SZ

	for APs on 110.0x
    
    ```bash
    in GUI you can enable Discovery options such as LWAPP or configure the SZ address
    ```

	for APs on Unleashed
	
    ```bash
    enable
	ap-mode
	set scg ip x.x.x.x
	get scg
    ```

!!! info ""

    #### creating registration Rule

    System > AP Settings > AP Registration > Create


!!! info ""

    #### Smartzone AP DISCOVERY process

	##### Discovery AP to SZ
	AP sends its status and capabilities including
	- HW & Firmware
	- Radio types
	- Encryption services support
			
	##### Discovery SZ to AP

	SZ status and capabilities including
	- Cluster Node address (Control & Data Plane)
	- SSH certificate
	- SZ firmware install (with dependencies)

    ##### next steps

    AP sends discover
    AP installs SSH cert
    AP waits in default Group

    DIR or CTL LED Indicator is used for AP controller communication
    
    ```bash
    Slow green flashing: no controller connection
    Fast green flash : firmware/config updating
    Solid green: AP connected to controller
    ```

!!! info ""

    #### Access Point Registration - Process

    ##### SZ High scale
    - AP sends discovery request
    - Install SSH Cert
    - AP waits in default AP Group in staging Zone (No firmware download at this point)

    ##### SZ Essentials
    - AP sends discovery request
    - Install SSH Cert
  
      - **Scenario 1**:
        - If Auto approval is disabled > AP will wait for approval
        - Once approval granted > AP goes into the default Zone within the Default Group and downloads the firmware

      - **Scenario 2**
        - If Auto approve enabled > AP joins Default Zone Default Group and downloads firmware


!!! info ""

    #### Access Point Registration - Completion

    ##### SZ High scale
    - AP moved to zone / Sub-Domain
    - Once AP approved it download the SZ FW and Zone Config from SZ
    - AP establishes Control tunnel (If configured, it will also establish - the Data tunnel connection)
    - AP reports health

    ##### SZ Essentials
    - AP moved to Zone
    - Once AP approved it downloads the Zone Config from SZ
    - AP establishes Control tunnel (If configured, it will also establish - the Data tunnel connection)
    - AP reports health
	
    ##### SZ AP DHCP Discovery

    - Discovery through DHCP > SZ address will be sent to all clients if option - 60 is used
    - Option 43 : Code 6
    - Option 60 : Ruckus CPE


!!! info ""

    #### SmartZone used Ports

    **UDP**

    - 123 : NTP
        
    **TCP**

    - 21   : FTP for AP upgrade
    - 22   : SSH for AP CLI connectivity
    - 91   : FTP for SmartZone to update 3.x, 100.x, or 110.x AP
    - 443  : New AP Registration
    - 8443 : SmartZone Web GUI

!!! info ""

    #### Event & Alarms

    Event & Alarms > Events
    You can see "sent a discovery request to SmartZone"
