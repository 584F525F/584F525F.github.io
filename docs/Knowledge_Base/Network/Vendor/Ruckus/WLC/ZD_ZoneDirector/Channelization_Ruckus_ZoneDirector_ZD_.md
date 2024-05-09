!!! info ""
    
    #### WLAN

    Select the WLAN you want to edit > click Edit
    Expand "Advanced Options"

    locate the following options:

    Background Scanning: uncheck
    Load Balancing: Check
    ![alt text](/Knowledge_Base/images/ZD_ZoneDirector_image.png)

    802.11d: Check
    ![alt text](/Knowledge_Base/images/ZD_ZoneDirector_image-1.png)

    OFDM Only: Check
    ![alt text](/Knowledge_Base/images/ZD_ZoneDirector_image-2.png)


    Depending on AP coverage this value needs to be changed as needed. If a client cannot achieve this minimum then you need to set at a lower value, you can start with 12 mbps
    ![alt text](/Knowledge_Base/images/ZD_ZoneDirector_image-3.png)

    Radio Resource Management: Check
    ![alt text](/Knowledge_Base/images/ZD_ZoneDirector_image-4.png)


!!! info ""
    
    #### Access Points

    Choose the AP Group > click Edit

    Select channel override for 2.4GHz band and choose channels 1,6,11
    Select channel override for 5GHz band and choose channels 36-165
    Make sure you have Channelization is set to 20 Mhz width for both bands
    ![alt text](/Knowledge_Base/images/ZD_ZoneDirector_image-5.png)


!!! info ""
    
    #### Services 
    
    Services & Profiles > Services
    Enable Self Healing

    Background Scanning > 2700 (45 MIN)

    ![zdc1](/Knowledge_Base/images/zdc1.png)

!!! example ""

    #### extra sources
    - [Background Scanning](https://docs.commscope.com/bundle/zd-10.5.1-userguide/page/GUID-B1DD91EA-5E77-4C3E-BE1F-5F8DB242F099.html)
    - [ZD1200 ZoneDirector 10.5.1 User Guide](/Knowledge_Base/images/ZD1200-ZoneDirector-10.5.1-User-Guide-RevB-20220120.pdf)
    - [ZoneDirector 10.5.1 Release Notes GA Refresh 4](/Knowledge_Base/images/ZoneDirector-10.5.1-Release-Notes-GA-Refresh-4-RevA-20230317.pdf)
