??? info "MCS"
    
    ### MCS Rate SNR RSSI Chart
    [MCS TABLE AND HOW TO USE IT](https://wlanprofessionals.com/mcs-table-and-how-to-use-it/)
    
    [mcsindex](https://mcsindex.net/)
    The MCS table evaluates the quality of the RF environment- the RF media that devices are working in, which is reflected in every single transmission.
    Every transmitter device, whether it be an AP or a client, will make an internal decision of which MCS it is going to use.
    MCS summarizes and categorizes Wi-Fi parameters such as modulation, coding scheme, guard interval, and channel width.
    ![alt text](</Knowledge_Base/images/MCS Rate SNR RSSI Chart 802.11n 802.11 ac.jpg>)
    **MCS Parameters**
    
    - High Throughput Modulation and Coding Scheme (HT-MCS)
      - Used by 802.11n. Represented by an integer in the range of 0-76.
    - Very High Throughput Modulation and Coding Scheme (VHT-MCS)
      - Used by 802.11ac. Represented by an integer in the range of 0-9.
    - Modulation Scheme
      - Defines the phase and amplitude required for bit computing, from BPSK to QPSK to 16-QAM, 64-QAM, and 256-QAM.
    - Coding
      - Rate of bits transferred and Forward Error Correction. A 1/2 Coding means two bits are transferred, and one is received. Minimizing the coding scheme would entail sending the data faster while losing robustness.
    - Data Width
      - Specifies the channel used: 20MHz, 40MHz, 80MHz, and 160MHz.
    - Guard Interval
      - Waiting time or pause between each packet transmission. 802.11n has 400ns, and 802.11ac has 800 ns. The smaller the guard interval, the faster the throughput.
    - Minimum SNR and RSSI
      - Determines the minimum SNR and RSSI required for a specific MSC index.
    **Using the MCS Table to determine the MCS index**
    
    - Define the capacity of the client device, such as the data width and Wi-Fi designation.
    - Determine and associate the range of such parameters in the table.
    For example, an 80MHz wide-capable client and supports 802.11ac. This means the AP and the client can support all data transfer defined by the range of the client device, from 6.5 MCS to 1300 MCS.
    ![alt text](/Knowledge_Base/images/WiFi_802_11_img_1.png)
    - After determining the MCS index, the client device will send a DHCP request to the radio chipset.
    - The AP’s radio will decode and demodulate the request. If no error occurs, it will send back an ACK with an MCS index supported by the client device. Every transmitter chooses which MCS to use.

??? info "Airtime"

    ### Airtime Utilization
    
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


!!! info "FCC Rules & Regulations"

    ### FCC Rules & Regulations 2.4 5.0 GHz Band Power Watt dBm Max

    [click to open PDF in new tab](</Knowledge_Base/images/FCC Rules & Regulations 2.4 5.0 GHz Band Power Watt dBm Max.pdf>)

    <embed src="/Knowledge_Base/images/FCC Rules & Regulations 2.4 5.0 GHz Band Power Watt dBm Max.pdf" type="application/pdf" style="min-height:100vh;width:100%">

??? info "RF"

    ### WiFi RF Spectrum

    ![alt text](/Knowledge_Base/images/wifi_80211_img_w0_1.png)

    ![alt text](/Knowledge_Base/images/wifi_80211_img_w0_9.png)

    !!! info ""

        #### WiFi 2.4GHz - 802.11n

        2.4 GHz band (802.11b/g/n) in North America, there are 11 channels of 20 MHz size allowed by the FCC. Some or all of channels 12-14 are allowed in some other countries, such as Japan. Unfortunately, the center frequencies of channels 1-13 are only 5 MHz apart, leading to only three non-overlapping channels (1, 6 and 11).

        ![alt text](/Knowledge_Base/images/wifi_80211_img_0.png)


    !!! info ""

        #### WiFi 5GHz - 802.11ac

        ![alt text](/Knowledge_Base/images/wifi_80211_img_1.png)

        ![alt text](/Knowledge_Base/images/wifi_80211_img_2.png)

        ![alt text](/Knowledge_Base/images/wifi_80211_img_3.png)

        ![alt text](/Knowledge_Base/images/wifi_80211_img_4.png)


    !!! info ""

        #### WiFi 6 & 6E - 802.11ax

        ![alt text](</Knowledge_Base/images/Low Power Indoor (LPI) Access Points in the 6 GHz Band.png>)

        ![alt text](/Knowledge_Base/images/wifi_80211_img_w0_0.png)

        **WiFi 5 vs WiFi 6**
        ![alt text](/Knowledge_Base/images/wifi_80211_img_w0_10.png)
        
        **Additional resources**

        - WiFi 6GHz Network Discovery [click to open PDF in new tab](/Knowledge_Base/images/wifi-6ghz-network-discovery.pdf)
        - WiFi 6E new Technology Features and Enhancements [click to open PDF in new tab](/Knowledge_Base/images/wi-fi-6e-new-technology-features-and-enhancements-(2022).pdf)
        - Reference Guide 802.11ax [click to open PDF in new tab](/Knowledge_Base/images/ReferenceGuide_80211ax.pdf)


    !!! info ""

        #### Great sources:

        - [WLAN Professionals](https://wlanprofessionals.com/)
        - [CWNP](https://www.cwnp.com/it-certification-training-resources/)

??? info "Terms"

    ### WiFi Terms

    #### WiFi Frames

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

    #### BSS Coloring
    A method for addressing medium contention overhead due to overlapping basic service set (OBSS). BSS color aims to uniquely identify different BSSs even though they are transmitting on the same channel. 802.11ax radios can differentiate between BSSs by adding a number (color) to the PHY and MAC headers. The same color bit indicates an intra-BSS. Different color bits indicate inter-BSS. Inter-BSS detection means that a listening radio may not necessarily have to defer. Adaptive CCA implementation could raise the signal detect (SD) threshold for inter-BSS frames while maintaining a lower threshold for intra-BSS traffic. BSS Color potentially decreases the channel contention problem resulting from existing 4 dB signal detect (SD) thresholds.

    #### BSS Min Rate

    Use this option to configure the minimum transmission rate supported by the WLAN. When OFDM Only is enabled, BSS Min Rate offers three options: Default, 12 Mbps, and 24 Mbps. If set to Default, Mgmt Tx rate is fixed at 6 Mbps. This option can also be used to prevent 802.11b clients from connecting, and to allow greater client density with higher data rates.

    If you have devices that *all* can do WPA2, use "ofdm-only", which will set the management frame min-rate to 6mb and refuse all CCK (802.11b/g only) clients

    If a device cannot achieve the min bss rate limit, the client device won't be able to connect to the WLAN in that area, they would have to move closer to the AP to get better rates.

    #### Mgmt Tx Rate
    
    Use this setting to configure the rate at which management frames are sent. The default is 2 Mbps. This option is only available if both OFDM Only and BSS Min Rate are disabled. (Otherwise, Mgmt Tx Rate is defined by those settings.)

    #### WiFi Backhaul
    Imagine you want to connected 2 buildings Network but you don't have the capability or means to run an Ethernet or Fiber cables between the 2 buildings, you can instead use WiFi Access Points to do the job.
    
    Using fixed **PTP** (Point To Point) or **PTMP** (Point To Multi Point) **Access Points** you can have two or more buildings Networks connected.

    ![alt text](/Knowledge_Base/images/WiFi_802_11_img_0.png)

    #### 802.11K

    **Transmit Power Control**:  The 802.11h amendment defined the use of transmit power
    control (TPC) for the 5 GHz band to reduce interference. Under 802.11k, TPC will also
    be used in other frequency bands and in areas governed by other regulatory agencies.
    
    **Client Statistics**:  Physical layer information, such as signal-to-noise ratio, signal
    strength, and data rates, can all be reported back to the access point or WLAN
    controller. MAC information, such as frame transmissions, retries, and errors, may all be
    reported back to the access point or WLAN controller as well.
    
    **Channel Statistics**:  Clients may gather noise-floor information based on any RF energy
    in the background of the channel and report this information back to the access point.
    Channel-load information may also be collected and sent to the AP. The access point or
    WLAN controller may use this information for channel management decisions.
    
    **Neighbor Reports**:  802.11k gave client stations the ability to learn from access points
    or WLAN controllers about other access points where the client stations might potentially roam. AP neighbor report information is shared among WLAN devices to improve
    roaming efficiency.


    #### 802.11 r-Fast Transition

    The fast basic service set transition (FT) amendment. The technology is more often referred to as fast-secure roaming because it defines faster handoffs when roaming occurs between cells in a WLAN using the strong security 56 Chapter 2 ■ IEEE 802.11 Standard and Amendments defined by a robust secure network (RSN). Be aware that there are multiple types of fastsecure roaming that are implemented by different vendors. These include CCKM, PKC, OKC, and fast session resumption.

    #### Roaming

    When a device moves through a Hotel and the device is connected to a WiFi network, the connection should seamlessly transition from Access Point to another on the same WLAN.


??? info "Power!"

    ### PoE/PoE+ (Power over Ethernet)

    This is a Technology that runs through Ethernet 802.3, the reason I am putting it here is that Wireless Access Point in this day and age get their power through PoE (there are exception though but those are far in between and you end up using something like a PoE Injector or Directly plug the AP into a wall outlet).

    ![alt text](/Knowledge_Base/images/wifi_80211_img_w0_2.png)


    #### Device detection and negotiation process

    This process is determined through either one of the following methods:
    - Hardware handshake or PoE handshake. There is another s
    - Software-based negotiation using LLDP (Link Layer Discovery Protocol), which is a L2 [data link layer protocol] for advertising network capabilities. 

    ![alt text](/Knowledge_Base/images/wifi_80211_img_w0_4.png)

    #### 802.3af PoE
    - maximum power of 15.4 watts
    - device type 1
    - 2-Pair PoE

    #### 802.3at PoE+
    - maximum power to 25.5 watts
    - device type 2
    - 2-Pair PoE

    #### 802.3bt UPoE Type 3
    - maximum power up 60 watts
    - 4-pair PoE

    #### 802.3bt UPoE+ Type 4
    - maximum power up to 100 W of DC power (71.3 W to each device)
    - 4-pair PoE

    Keep in mind that the Switch doesn't provide infinite watts. For example if the Switch specs provides max 300 watts through PoE and it's a 24 port Switch, you cannot connect 24 PoE devices that require 15.4 watts each. It's simple math 24 X 15.4 = 369.2, this exceeds the Switch Maximum Power output.
    In reality APs don't consume exactly 15.4 watts, this can vary based on AP and demand.

    #### Extra resources
    - [Introduction to PoE and the IEEE802.3af and 802.3at Standards](https://ieee.li/pdf/viewgraphs/introduction_to_poe_802.3af_802.3at.pdf)
    - [Understanding the IEEE 8023bt PoE Standard](https://www.skyworksinc.com/-/media/SkyWorks/SL/documents/public/white-papers/understanding-the-ieee-8023bt-poe-standard.pdf)


!!! info "Client device"

    ### Clients devices WiFi capabilities
    
    Not all Client devices support the same WiFi Standards you might have configured You can check the [Clients devices WiFi capabilities](https://docs.google.com/spreadsheets/d/1qpQYyIiS9J8wMa7iD0nEMvZxTB7X1i4gEWy19L0N05o/edit#gid=0)

    How to tell if a client device is using MAC Randomization - Private Address
    2nd significant bit in the most significant octet you set to 1 that means the 2nd character in the mac address can be one of 4
    
    ```bash
    X2:XX:XX:XX:XX:XX
    X6:XX:XX:XX:XX:XX
    XA:XX:XX:XX:XX:XX
    XE:XX:XX:XX:XX:XX
    ```
