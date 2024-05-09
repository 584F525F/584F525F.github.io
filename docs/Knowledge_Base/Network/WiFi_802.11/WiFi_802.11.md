!!! info ""

    ### MCS Rate SNR RSSI Chart 802.11n 802.11 ac

    ![alt text](</Knowledge_Base/images/MCS Rate SNR RSSI Chart 802.11n 802.11 ac.jpg>)

    ### Airtime Utilization - MSC Index - Modulation - Coding Index 
    
    !!! warning ""
        Channel Utilization should not exceed %70, if it goes beyond %80 then there is a big chance something that's not WiFi is interfering.

    **What can cause it?**
    - Application usage
    - Slow Data Rates - Check device's supported 802.11
    - Retransmissions
    - More Devices
    - Non-WiFi Interference

    **What to consider?**
    - Lower number of SSIDs can help with improving Airtime Utilization, Try less than 4 SSIDs. Reason is that you have a lot of Management data that will be consuming time instead of actual Data.
    - Capabilities of device and data rates
    - Play around with min bss rates on both bands and eliminate legacy device, removing 802.11 or b maybe
    - min rate 12 Mbps
    - Channel width 20 or 40 (try to stick with 20MHz Channel width, especially on the 2.4GHz band)
    Enable extra channels on 5GHz if needed like DFS
    - AP Placement
    - Transmit power
    - Check the [MCS Index, Modulation and Coding Index](https://mcsindex.net/)

    **Some of the WiFi Frames**
    - MAC Frame
    - Control
    - Management > Beacon frames
    - Data

    ```bash
    Type Value	Type Description	Subtype Value	Subtype Description
    00			Management			0000			Association Request
    00			Management			0001			Association Response
    00			Management			0010			Reassociation Request
    00			Management			0011			Reassociation Response
    00			Management			0100			Probe Request
    00			Management			0101			Probe Response
    00			Management			0110			Timing Advertisement
    00			Management			0111			Reserved
    00			Management			1000			Beacon
    00			Management			1001			ATIM
    00			Management			1010			Disassociation
    00			Management			1011			Authentication
    00			Management			1100			Deauthentication
    00			Management			1101			Action
    00			Management			1110			Action No Ack (NACK)
    00			Management			1111			Reserved


    01			Control				0000-0001		Reserved
    01			Control				0010			Trigger[3]
    01			Control				0011			TACK
    01			Control				0100			Beamforming Report Poll
    01			Control				0101			VHT/HE NDP Announcement
    01			Control				0110			Control Frame Extension
    01			Control				0111			Control Wrapper
    01			Control				1000			Block Ack Request (BAR)
    01			Control				1001			Block Ack (BA)
    01			Control				1010			PS-Poll
    01			Control				1011			RTS
    01			Control				1100			CTS
    01			Control				1101			ACK
    01			Control				1110			CF-End
    01			Control				1111			CF-End + CF-ACK


    10			Data				0000			Data
    10			Data				0001			Reserved
    10			Data				0010			Reserved
    10			Data				0011			Reserved
    10			Data				0100			Null (no data)
    10			Data				0101			Reserved
    10			Data				0110			Reserved
    10			Data				0111			Reserved
    10			Data				1000			QoS Data
    10			Data				1001			QoS Data + CF-ACK
    10			Data				1010			QoS Data + CF-Poll
    10			Data				1011			QoS Data + CF-ACK + CF-Poll
    10			Data				1100			QoS Null (no data)
    10			Data				1101			Reserved
    10			Data				1110			QoS CF-Poll (no data)
    10			Data				1111			QoS CF-ACK + CF-Poll (no data)
    11			Extension			0000			DMG Beacon
    11			Extension			0001			S1G Beacon
    11			Extension			0010-1111		Reserved

    ```

    for more details about the WiFi frame, check this resource out [802.11 Frame Types and Formats](https://howiwifi.com/2020/07/13/802-11-frame-types-and-formats/)


!!! info ""

    ### FCC Rules & Regulations 2.4 5.0 GHz Band Power Watt dBm Max

    [click to open PDF in new tab](</Knowledge_Base/images/FCC Rules & Regulations 2.4 5.0 GHz Band Power Watt dBm Max.pdf>)

    <embed src="/Knowledge_Base/images/FCC Rules & Regulations 2.4 5.0 GHz Band Power Watt dBm Max.pdf" type="application/pdf" style="min-height:100vh;width:100%">

!!! info ""

    ### WiFi 2.4GHz band

    2.4 GHz band (802.11b/g/n) in North America, there are 11 channels of 20 MHz size allowed by the FCC. Some or all of channels 12-14 are allowed in some other countries, such as Japan. Unfortunately, the center frequencies of channels 1-13 are only 5 MHz apart, leading to only three non-overlapping channels (1, 6 and 11).

    ![alt text](/Knowledge_Base/images/wifi_80211_img_0.png)


!!! info ""

    ### WiFi 5GHz band

    ![alt text](/Knowledge_Base/images/wifi_80211_img_1.png)

    ![alt text](/Knowledge_Base/images/wifi_80211_img_2.png)

    ![alt text](/Knowledge_Base/images/wifi_80211_img_3.png)

    ![alt text](/Knowledge_Base/images/wifi_80211_img_4.png)
    

!!! info ""

    ### WiFi 6GHz band

    ![alt text](<Low Power Indoor (LPI) Access Points in the 6 GHz Band.png>)


!!! info ""

    ### WiFi 6 band - 802.11ax

    ![alt text](/Knowledge_Base/images/wifi_80211_img_6.png)

    
    [click to open PDF in new tab](/Knowledge_Base/images/ReferenceGuide_80211ax.pdf)

    <embed src="/Knowledge_Base/images/ReferenceGuide_80211ax.pdf" type="application/pdf" style="min-height:100vh;width:100%">



    
    

