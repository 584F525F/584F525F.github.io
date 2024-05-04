!!! info ""

    ### shodan-dorks

    [shodan-dorks github](https://github.com/dootss/shodan-dorks)

    ??? info "Cameras"

        [General camera search.](https://www.shodan.io/search?query=camera)  
        `camera` - 3,663,091 results  


        [Hikvision IP Cameras.](https://www.shodan.io/search?query=product%3A%22Hikvision%20IP%20Camera%22)  
        `product:"Hikvision IP Camera"` - 2,710,304 results  
        Backdoor exploit at https://ipvm.com/reports/hik-exploit

        [Webcams running on IPCam Client.](https://www.shodan.io/search?query=title%3A%22IPCam%20Client%22)  
        `title:"IPCam Client"` - 60,012 results  


        [Older webcams running on GeoVision.](https://www.shodan.io/search?query=server%3A%20GeoHttpServer)  
        `server: GeoHttpServer` - 40,659 results  


        [Avigilion-brand camera/monitoring devices.](https://www.shodan.io/search?query=title%3A%22Avigilon%22)  
        `title:"Avigilon"` - 18,951 results  


        [Vivotek IP cameras.](https://www.shodan.io/search?query=server%3A%20VVTK-HTTP-Server)  
        `server: VVTK-HTTP-Server` - 15,333 results  


        [DVR CCTV cameras accessible via http.](https://www.shodan.io/search?query=200%20ok%20dvr%20port%3A%2281%22)  
        `200 ok dvr port:"81"` - 9,409 results  


        [Netwave-make IP cameras.](https://www.shodan.io/search?query=Netwave%20IP%20Camera%20Content-Length%3A%202574)  
        `Netwave IP Camera Content-Length: 2574` - 1,313 results  


        [A UK-based IP camera provider.](https://www.shodan.io/search?query=WWW-Authenticate%3A%20%22Merit%20LILIN%20Ent.%20Co.%2C%20Ltd.%22)  
        `WWW-Authenticate: "Merit LILIN Ent. Co., Ltd."` - 1,208 results  


        [Yet another WebCAM software.](https://www.shodan.io/search?query=product%3A%22Yawcam%20webcam%20viewer%20httpd%22)  
        `product:"Yawcam webcam viewer httpd"` - 613 results  


        [UI3 - the HTML5 web interface for Blue Iris.](https://www.shodan.io/search?query=title%3A%22ui3%20-%22)  
        `title:"ui3 -"` - 496 results  


        [Unsecured Linksys webcams.](https://www.shodan.io/search?query=title%3A%22%2Btm01%2B%22)  
        `title:"+tm01+"` - 447 results  


        [Various IP camera/video management system products.](https://www.shodan.io/search?query=ACTi)  
        `ACTi` - 385 results  


        [Webcams with screenshots.](https://www.shodan.io/search?query=webcam%20has_screenshot%3Atrue)  
        `webcam has_screenshot:true` - 199 results  


        [Webcams running on webcamXP](https://www.shodan.io/search?query=server%3A%20webcamxp)  
        `server: webcamxp` - 162 results  


        [Webcams running on webcam 7.](https://www.shodan.io/search?query=server%3A%20%22webcam%207%22)  
        `server: "webcam 7"` - 89 results  


        [IP Webcams with screenshots.](https://www.shodan.io/search?query=has_screenshot%3Atrue%20IP%20Webcam)  
        `has_screenshot:true IP Webcam` - 78 results  


        [Webcams running on Blue Iris.](https://www.shodan.io/search?query=title%3A%22blue%20iris%20remote%20view%22)  
        `title:"blue iris remote view"` - 35 results  


        [Canon-manufactured megapixel security cameras.](https://www.shodan.io/search?query=title%3A%22Network%20Camera%20VB-M600%22)  
        `title:"Network Camera VB-M600"` - 33 results  


        [i-Catcher IP-based CCTV systems.](https://www.shodan.io/search?query=server%3A%20%22i-Catcher%20Console%22)  
        `server: "i-Catcher Console"` - 25 results  


        [Linksys WVC80N cameras.](https://www.shodan.io/search?query=WVC80N)  
        `WVC80N` - 24 results  


    ??? info "Industrial Control Systems"

        [EtherNet/IP](https://www.shodan.io/search?query=port%3A44818)  
        `port:44818` - 536,021 results  


        [S7](https://www.shodan.io/search?query=port%3A102)  
        `port:102` - 515,940 results  


        [Modbus](https://www.shodan.io/search?query=port%3A502)  
        `port:502` - 507,869 results  


        [BACnet](https://www.shodan.io/search?query=port%3A47808)  
        `port:47808` - 45,102 results  


        [Niagara Fox](https://www.shodan.io/search?query=port%3A1911%2C4911%20product%3ANiagara)  
        `port:1911,4911 product:Niagara` - 9,257 results  


        [VNC Servers](https://www.shodan.io/search?query=%22authentication%20disabled%22%20%22RFB%20003.008%22)  
        `"authentication disabled" "RFB 003.008"` - 6,623 results  
        While not always 100% guaranteed to be a system, lots of embedded systems can show up here, along with personal systems.

        [More VNC Servers](https://www.shodan.io/search?query=%22authentication%20disabled%22%20port%3A5900%2C5901)  
        `"authentication disabled" port:5900,5901` - 6,321 results  
        Another search term for VNC servers - most are on port 5900 or 5901 as these are VNC display ports.

        [Gas Station Pump Controllers](https://www.shodan.io/search?query=%22in-tank%20inventory%22%20port%3A10001)  
        `"in-tank inventory" port:10001` - 5,998 results  
        Find gas station pump controllers with accessible inventory data.

        [IEC 60870-5-104](https://www.shodan.io/search?query=port%3A2404%20asdu%20address)  
        `port:2404 asdu address` - 3,488 results  


        [Siemens Industrial Automation](https://www.shodan.io/search?query=%22Siemens%2C%20SIMATIC%22%20port%3A161)  
        `"Siemens, SIMATIC" port:161` - 3,024 results  


        [Omron FINS](https://www.shodan.io/search?query=port%3A9600%20response%20code)  
        `port:9600 response code` - 1,835 results  


        [DICOM Medical X-Ray Machines](https://www.shodan.io/search?query=%22DICOM%20Server%20Response%22%20port%3A104)  
        `"DICOM Server Response" port:104` - 1,818 results  


        [DNP3](https://www.shodan.io/search?query=port%3A20000%20source%20address)  
        `port:20000 source address` - 1,007 results  


        [PCWorx](https://www.shodan.io/search?query=port%3A1962%20PLC)  
        `port:1962 PLC` - 980 results  


        [XZERES Wind Turbine](https://www.shodan.io/search?query=title%3A%22xzeres%20wind%22)  
        `title:"xzeres wind"` - 582 results  


        [ProConOS](https://www.shodan.io/search?query=port%3A20547%20PLC)  
        `port:20547 PLC` - 500 results  


        [MELSEC-Q](https://www.shodan.io/search?query=port%3A5006%2C5007%20product%3Amitsubishi)  
        `port:5006,5007 product:mitsubishi` - 255 results  


        [Door / Lock Access Controllers](https://www.shodan.io/search?query=%22HID%20VertX%22%20port%3A4070)  
        `"HID VertX" port:4070` - 186 results  


        [C4 Max Commercial Vehicle GPS Trackers](https://www.shodan.io/search?query=%5B1m%5B35mWelcome%20on%20console)  
        `[1m[35mWelcome on console` - 75 results  


        [Electric Vehicle Chargers](https://www.shodan.io/search?query=%22Server%3A%20gSOAP/2.8%22%20%22Content-Length%3A%20583%22)  
        `"Server: gSOAP/2.8" "Content-Length: 583"` - 42 results  


        [Nordex Wind Turbine Farms](https://www.shodan.io/search?query=http.title%3A%22Nordex%20Control%22%20%22Windows%202000%205.0%20x86%22%20%22Jetty/3.1%20%28JSP%201.1%3B%20Servlet%202.2%3B%20java%201.6.0_14%29%22)  
        `http.title:"Nordex Control" "Windows 2000 5.0 x86" "Jetty/3.1 (JSP 1.1; Servlet 2.2; java 1.6.0_14)"` - 36 results  


        [GaugeTech Electricity Meters](https://www.shodan.io/search?query=%22Server%3A%20EIG%20Embedded%20Web%20Server%22%20%22200%20Document%20follows%22)  
        `"Server: EIG Embedded Web Server" "200 Document follows"` - 33 results  


        [Voting Machines in the United States](https://www.shodan.io/search?query=%22voter%20system%20serial%22%20country%3AUS)  
        `"voter system serial" country:US` - 23 results  


        [Traffic Light Controllers / Red Light Cameras](https://www.shodan.io/search?query=mikrotik%20streetlight)  
        `mikrotik streetlight` - 21 results  


        [Open ATM](https://www.shodan.io/search?query=NCR%20Port%3A%22161%22)  
        `NCR Port:"161"` - 21 results  


        [CAREL PlantVisor Refrigeration Units](https://www.shodan.io/search?query=%22Server%3A%20CarelDataServer%22%20%22200%20Document%20follows%22)  
        `"Server: CarelDataServer" "200 Document follows"` - 13 results  


        [HART-IP](https://www.shodan.io/search?query=port%3A5094%20hart-ip)  
        `port:5094 hart-ip` - 12 results  


        [Siemens HVAC Controllers](https://www.shodan.io/search?query=%22Server%3A%20Microsoft-WinCE%22%20%22Content-Length%3A%2012581%22)  
        `"Server: Microsoft-WinCE" "Content-Length: 12581"` - 6 results  


        [Fuel Pumps connected to internet](https://www.shodan.io/search?query=%22privileged%20command%22%20GET)  
        `"privileged command" GET` - 5 results  


        [Samsung Electronic Billboards](https://www.shodan.io/search?query=Server%3A%20Prismview%20Player)  
        `Server: Prismview Player` - 3 results  
        Search for electronic billboards managed by Prismview servers.

        [Automatic License Plate Readers](https://www.shodan.io/search?query=P372%20%22ANPR%20enabled%22)  
        `P372 "ANPR enabled"` - 2 results  


        [Submarine Mission Control Dashboards](https://www.shodan.io/search?query=title%3A%22Slocum%20Fleet%20Mission%20Control%22)  
        `title:"Slocum Fleet Mission Control"` - 1 result  


        [Tesla Powerpack charging Status](https://www.shodan.io/search?query=http.title%3A%22Tesla%20PowerPack%20System%22%20http.component%3A%22d3%22%20-ga3ca4f2)  
        `http.title:"Tesla PowerPack System" http.component:"d3" -ga3ca4f2` - 1 result  

    ??? info "Network Infastructure"

        [General MySQL Database Search](https://www.shodan.io/search?query=product%3AMySQL)  
        `product:MySQL` - 3,319,173 results  


        [Remote PostgreSQL Connections](https://www.shodan.io/search?query=port%3A5432%20PostgreSQL)  
        `port:5432 PostgreSQL` - 761,333 results  


        [MongoDB Server Information on Default Port](https://www.shodan.io/search?query=%22MongoDB%20Server%20Information%22%20port%3A27017)  
        `"MongoDB Server Information" port:27017` - 104,009 results  


        [Default MongoDB Instances](https://www.shodan.io/search?query=mongodb%20port%3A27017)  
        `mongodb port:27017` - 102,910 results  


        [Open Elasticsearch Databases](https://www.shodan.io/search?query=port%3A%229200%22%20all%3Aelastic)  
        `port:"9200" all:elastic` - 30,464 results  


        [Jenkins CI](https://www.shodan.io/search?query=%22X-Jenkins%22%20%22Set-Cookie%3A%20JSESSIONID%22%20http.title%3A%22Dashboard%22)  
        `"X-Jenkins" "Set-Cookie: JSESSIONID" http.title:"Dashboard"` - 14,767 results  


        [Cisco Smart Install](https://www.shodan.io/search?query=smart%20install%20client%20active)  
        `smart install client active` - 7,099 results  


        [Listed Apache CouchDB](https://www.shodan.io/search?query=product%3A%22CouchDB%22)  
        `product:"CouchDB"` - 4,670 results  


        [Android Root Bridges](https://www.shodan.io/search?query=%22Android%20Debug%20Bridge%22%20%22Device%22%20port%3A5555)  
        `"Android Debug Bridge" "Device" port:5555` - 4,117 results  


        [Polycom Video Conferencing](https://www.shodan.io/search?query=http.title%3A%22-%20Polycom%22%20%22Server%3A%20lighttpd%22)  
        `http.title:"- Polycom" "Server: lighttpd"` - 3,625 results  


        [Pi-hole Open DNS Servers](https://www.shodan.io/search?query=%22dnsmasq-pi-hole%22%20%22Recursion%3A%20enabled%22)  
        `"dnsmasq-pi-hole" "Recursion: enabled"` - 2,960 results  


        [Lantronix Serial-to-Ethernet Adapter Leaking Telnet Passwords](https://www.shodan.io/search?query=Lantronix%20password%20port%3A30718%20-secured)  
        `Lantronix password port:30718 -secured` - 644 results  


        [Already Logged-In as root via Telnet](https://www.shodan.io/search?query=%22root%40%22%20port%3A23%20-login%20-password%20-name%20-Session)  
        `"root@" port:23 -login -password -name -Session` - 581 results  


        [Accessible Kibana Dashboards](https://www.shodan.io/search?query=kibana%20content-length%3A217)  
        `kibana content-length:217` - 535 results  


        [Exposed MongoDB Express Web Interfaces](https://www.shodan.io/search?query=%22Set-Cookie%3A%20mongo-express%3D%22%20%22200%20OK%22)  
        `"Set-Cookie: mongo-express=" "200 OK"` - 395 results  


        [Citrix Virtual Apps](https://www.shodan.io/search?query=%22Citrix%20Applications%3A%22%20port%3A1604)  
        `"Citrix Applications:" port:1604` - 300 results  


        [PBX IP Phone Gateways](https://www.shodan.io/search?query=PBX%20%22gateway%20console%22%20-password%20port%3A23)  
        `PBX "gateway console" -password port:23` - 179 results  


        [Docker Private Registries](https://www.shodan.io/search?query=%22Docker-Distribution-Api-Version%3A%20registry%22%20%22200%20OK%22%20-gitlab)  
        `"Docker-Distribution-Api-Version: registry" "200 OK" -gitlab` - 141 results  


        [Telnet Configuration](https://www.shodan.io/search?query=%22Polycom%20Command%20Shell%22%20-failed%20port%3A23)  
        `"Polycom Command Shell" -failed port:23` - 39 results  


        [Weave Scope Dashboards](https://www.shodan.io/search?query=title%3A%22Weave%20Scope%22%20http.favicon.hash%3A567176827)  
        `title:"Weave Scope" http.favicon.hash:567176827` - 13 results  


        [Vulnerable CouchDB Instances](https://www.shodan.io/search?query=port%3A%225984%22%2BServer%3A%20%22CouchDB/2.1.0%22)  
        `port:"5984"+Server: "CouchDB/2.1.0"` - 5 results  


    ??? info "Printers"

        [General Printer Search](https://www.shodan.io/search?query=printer)  
        `printer` - 86,286 results  


        [HP Printers Remote Restart](https://www.shodan.io/search?query=port%3A161%20hp)  
        `port:161 hp` - 11,002 results  


        [Canon Printer HTTP Servers](https://www.shodan.io/search?query=Server%3A%20CANON%20HTTP%20Server)  
        `Server: CANON HTTP Server` - 9,818 results  


        [HTTP Accessible Epson Printers](https://www.shodan.io/search?query=http%20200%20server%20epson%20-upnp)  
        `http 200 server epson -upnp` - 2,016 results  


        [Samsung Printers with SyncThru Web Service](https://www.shodan.io/search?query=title%3A%22syncthru%20web%20service%22)  
        `title:"syncthru web service"` - 998 results  


        [Unsecured Telnet Access to Printers](https://www.shodan.io/search?query=port%3A23%20%22Password%20is%20not%20set%22)  
        `port:23 "Password is not set"` - 414 results  


        [Remote Access to Xerox Printers](https://www.shodan.io/search?query=ssl%3A%22Xerox%20Generic%20Root%22)  
        `ssl:"Xerox Generic Root"` - 371 results  


        [Epson Printers via HTTP Server](https://www.shodan.io/search?query=%22Server%3A%20EPSON-HTTP%22%20%22200%20OK%22)  
        `"Server: EPSON-HTTP" "200 OK"` - 322 results  


        [HP LaserJet Printers via HTTP](https://www.shodan.io/search?query=%22HP-ChaiSOE%22%20port%3A%2280%22)  
        `"HP-ChaiSOE" port:"80"` - 163 results  


        [Lexmark Printer Control Panels](https://www.shodan.io/search?query=Printer%20Type%3A%20Lexmark)  
        `Printer Type: Lexmark` - 157 results  


        [Brother Printers Admin Interface](https://www.shodan.io/search?query=%22Location%3A%20/main/main.html%22%20debut)  
        `"Location: /main/main.html" debut` - 68 results  


        [Printers with FTP Access](https://www.shodan.io/search?query=Laser%20Printer%20FTP%20Server)  
        `Laser Printer FTP Server` - 4 results  


    ??? info "Files and Directories"

        [Open Lists of Files and Directories](https://www.shodan.io/search?query=http.title%3A%22Index%20of%20/%22)  
        `http.title:"Index of /"` - 366,845 results  


        [Filezilla FTP](https://www.shodan.io/search?query=filezilla%20port%3A%2221%22)  
        `filezilla port:"21"` - 254,717 results  


        [Samba Shares with Authentication Disabled](https://www.shodan.io/search?query=%22Authentication%3A%20disabled%22%20port%3A445%20product%3A%22Samba%22)  
        `"Authentication: disabled" port:445 product:"Samba"` - 210,681 results  


        [Open Lists on Port 80](https://www.shodan.io/search?query=port%3A80%20title%3A%22Index%20of%20/%22)  
        `port:80 title:"Index of /"` - 141,689 results  


        [FTP Access Without Credentials](https://www.shodan.io/search?query=%22220%22%20%22230%20Login%20successful.%22%20port%3A21)  
        `"220" "230 Login successful." port:21` - 62,727 results  


        [Anonymous Access Allowed FTP](https://www.shodan.io/search?query=%22Anonymous%20access%20allowed%22%20port%3A%2221%22)  
        `"Anonymous access allowed" port:"21"` - 32,821 results  


        [NDMP on FTP Port 10000](https://www.shodan.io/search?query=ftp%20port%3A%2210000%22)  
        `ftp port:"10000"` - 6,011 results  


        [Vulnerable vsftpd Service](https://www.shodan.io/search?query=vsftpd%202.3.4)  
        `vsftpd 2.3.4` - 2,954 results  


        [QuickBooks Files Shared Over Network](https://www.shodan.io/search?query=%22QuickBooks%20files%20OverNetwork%22%20-unix%20port%3A445)  
        `"QuickBooks files OverNetwork" -unix port:445` - 42 results  


    ??? info "Compromised devices and websites"

        [General Hacked Label Search](https://www.shodan.io/search?query=hacked)  
        `hacked` - 1,723 results  


        [Compromised Legacy Systems on Port 4444](https://www.shodan.io/search?query=port%3A4444%20system32)  
        `port:4444 system32` - 1,147 results  


        [Compromised Routers Labeled HACKED-ROUTER](https://www.shodan.io/search?query=HACKED-ROUTER)  
        `HACKED-ROUTER` - 762 results  


        [Compromised Routers](https://www.shodan.io/search?query=hacked-router-help-sos)  
        `hacked-router-help-sos` - 750 results  


        [Hacked By in HTTP Title](https://www.shodan.io/search?query=http.title%3A%22Hacked%20by%22)  
        `http.title:"Hacked by"` - 519 results  


        [Variation of Hacked By Label Search](https://www.shodan.io/search?query=hacked%20by)  
        `hacked by` - 269 results  


        [Compromised Hosts Advertising Default Password](https://www.shodan.io/search?query=HACKED-ROUTER-HELP-SOS-HAD-DEFAULT-PASSWORD)  
        `HACKED-ROUTER-HELP-SOS-HAD-DEFAULT-PASSWORD` - 102 results  


        [Compromised FTP Servers](https://www.shodan.io/search?query=HACKED%20FTP%20server)  
        `HACKED FTP server` - 68 results  


        [Ransomware Infected RDP Services](https://www.shodan.io/search?query=%22attention%22%20%22encrypted%22%20port%3A3389)  
        `"attention" "encrypted" port:3389` - 9 results  


        [Owned By Label in HTTP Title](https://www.shodan.io/search?query=http.title%3A%220wn3d%20by%22)  
        `http.title:"0wn3d by"` - 6 results  


        [Bitcoin Ransomware with Screenshot](https://www.shodan.io/search?query=bitcoin%20has_screenshot%3Atrue)  
        `bitcoin has_screenshot:true` - 2 results  


    ??? info "Miscellaneous"

        [General Dashboard Interfaces](https://www.shodan.io/search?query=http.title%3A%22dashboard%22)  
        `http.title:"dashboard"` - 157,047 results  


        [Control Panel Access Points](https://www.shodan.io/search?query=http.title%3A%22control%20panel%22)  
        `http.title:"control panel"` - 64,207 results  


        [Minecraft Servers](https://www.shodan.io/search?query=%22Minecraft%20Server%22%20%22protocol%20340%22%20port%3A25565)  
        `"Minecraft Server" "protocol 340" port:25565` - 10,652 results  


        [Tesla-related Interfaces](https://www.shodan.io/search?query=http.title%3A%22Tesla%22)  
        `http.title:"Tesla"` - 587 results  


        [Everything in North Korea](https://www.shodan.io/search?query=net%3A175.45.176.0/22%2C210.52.109.0/24%2C77.94.35.0/24)  
        `net:175.45.176.0/22,210.52.109.0/24,77.94.35.0/24` - 44 results  


        [EIG Electricity Meters](https://www.shodan.io/search?query=%22Server%3A%20EIG%20Embedded%20Web%20Server%22%20%22200%20Document%20follows%22)  
        `"Server: EIG Embedded Web Server" "200 Document follows"` - 33 results  


        [Misconfigured WordPress Installations](https://www.shodan.io/search?query=http.html%3A%22%2A%20The%20wp-config.php%20creation%20script%20uses%20this%20file%22)  
        `http.html:"* The wp-config.php creation script uses this file"` - 10 results  


        [Ethereum Miners](https://www.shodan.io/search?query=ETH%20-%20Total%20speed)  
        `ETH - Total speed` - 1 result  


!!! info ""

    ### apidork

    [apidork](https://github.com/sameerfakhoury/apidork)

    ```bash
    git clone https://github.com/sameerfakhoury/apidork.git
    cd apidork
    pip install -r requirements.txt
    python3 apidork.py
    ```

    now you are ready to use the tool and check each option with the corresponding information to use with

    usage

    Syntax: python3 apidork.py -option1 "value1" -option2 "value2" Options to use:

    ```bash
    1. username search: -u "user_name" -- example: python3 apidork.py -u "example"                                                              
    2. files related to domain: -d "domain_name" -f "file_extension" -- example: python3 apidork.py -d "example.com" -f "pdf"                   
    3. text in website: -url "full_url" -t "keyword" -- example: python3 apidork.py -url "https://example.com/index.html" -t "helloword"        
    4. restrict search to domain : -d "domain_name" -- example: python3 apidork.py -d "xxx.xxx.xx"                                              
    5. links title with keyword: -k "title_keyword" -- example: python3 apidork.py -k "xxxxxxxxxx"                                            
    6. extract location information: -lat "latitude" -lon "longitude" -- example: python3 apidork.py -lat "xx.xxx..." -lon "xx.xxx..."          
    7. extract location coordinates: -l "location_name" -- example: python3 apidork.py -l "xxxx xxx xx ..."                                     
    8. extract IP informations: -ip "ip" -- example: python3 apidork.py -ip "x.x.x.x"                                                           
    9. check your public IP: -myip -- example: python3 apidork.py -myip
    10. extract Zip/postal code informations: -c "country" -z "zipcode" -- example: python3 -c "xx" -z "xxxxx"                                  
    ```


!!! info ""

    ### Dorks eye

    [dorks eye - hackingpassion](https://hackingpassion.com/dorks-eye-google-hacking-dork-scraping-and-searching-script/)
    [dorks eye - github](https://github.com/Bullseye0/google_dork_list?tab=readme-ov-file)


!!! info ""

    [pagodo github](https://github.com/opsdisk/pagodo)

    

!!! info ""

    ### DorkFinder

    [DorkFinder- github](https://github.com/glavstroy/DorkFinder?tab=readme-ov-file)

    #### Install on Linux
    
    ```bash
    git clone https://github.com/glavstroy/DorkFinder
    cd DorkFinder
    pip install -r requirements
    ```

    #### Install on Docker

    ```bash
    git clone https://github.com/glavstroy/DorkFinder
    cd DorkFinder
    sudo docker build . -t dorkfinder
    sudo docker run -it --rm dorkfinder
    ```

    #### Switches/Flags

    |Flag | Description|
    |:-|:-|
    |-h/--help	|show this help message and exit|
    |-t	|enter the target domain|
    |-o	|print to output.txt|

    #### Usage

    ```bash
    python3 dorkfinder.py -t example.com -o
    ```



