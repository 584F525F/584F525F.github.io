!!! info ""

    EIRP (dBm) = Conducted Power (dBm) + Antenna Gain (dBi) – Cable loss (dB)

    Max EIRP allowed by FCC on Access Points

    2.4 GHz Channels 1 – 11 (36 dBm)
    5 GHz U-NII-1 channels 36 – 48 (36 dBm)
    5 GHz U-NII-2A channels 52 – 64 (30 dBm)
    5 GHz U-NII-2C channels 100 – 144 (30 dBm)
    5 GHz U-NII-3 channels 149 – 165 (36 dBm)

    Antenna Gain
    This is where Ruckus shines with the Beamflex gain. Beamflex adaptive antenna will get you approx. 3 dBi gain per 2 radio chains on most models. This will be added to the conductive power you set on the management interface and will make sure the EIRP is less than the FCC limit.

!!! info ""

    #### How to find the conducted power of your Ruckus Unleashed AP?

    run the below command on WAP

    ```bash
    ruckus> en
    ruckus# debug
    ruckus(debug)# rksap_cli -A -s “iwconfig”
    ```

    Below is a H510 AP configured with maximum Tx power. It shows 2.4 GHz using Tx power as 16 dBm and 5 GHz at 19 dBm.

    ![alt text](/Knowledge_Base/images//Knowledge_Base/images/Ruckus_WAP_image.png)

    R710 shows 2.4 GHz at 22 dBm and 5 GHz at 20 dBm.
    
    ![alt text](/Knowledge_Base/images/Ruckus_WAP_image-1.png)

!!! info ""

    #### How to find the conducted power of your Ruckus SmartZone AP?

    If you want to find the same Tx information in SZ-managed APs, you will need to access the shell mode of the AP and execute the below command:

    ```bash
    iwconfig wifi0
    wifi0     wifi0  Frequency:2.462 GHz  Tx-Power:23 dBm
    ```

    The above command shows the Tx power of the 2.4 GHz radio of an Access point.

    remember to include the beamflex gain when you do a predictive design or when you configure the Tx power settings. 

    ```bash
    iwconfig wifi0
    Require shell access to the AP, TAC required
    ```

!!! info ""

    #### The Rule of 3

    If you raise the dBm value by “3″ you double the mW value

    ```bash
    0dBm = 1mW
    3dBm = 2mW
    6dBm = 4mW
    9dBm = 8mW
    12dBm = 16mW
    15dBm = 32mW
    18dBm = 64mW
    21dBm = 128mW
    24dBm = 256mW
    27dBm = 512mW
    30dBm = 1024mW (5GHz Band B legal limit)
    33dBm = 2048mW
    36dBm = 4096mW (5GHz Band C legal limit)
    ```

!!! info ""

    #### The Rule of 10
    If you raise the dBm value by “10″ you multiply the mW value by 10:

    ```bash
    0dBm = 1mW
    10dBm = 10mW
    20dBm = 100mW
    30dBm = 1000mW (5GHz Band B legal limit)
    40dBm = 10000mW (Over the 5GHz Band C legal limit)
    ```

!!! info ""

    "support shell command"

    below command is what support uses to get into shell, they then would have to enter an encrypted phrase generated based on device S/N

    ```shell
    !v54!
    xv11e2UPjEmTCx806HutA85XE1su4pKzJgPuCEod0P4UQGwq8Ogx8QtWwxUViu7
    ```

!!! info ""

    #### Actual WAP Power vs datasheet

    I was working a case about a year ago channelizaing over 100 WAPs at this single location, i had to set the power on each WAP seperatly based on our ekahau WiFi Survey report, i am not one to do such task from GUI, therefor I scripted the whole thing to run on the SmartZone.

    Anyway, I found that after settings the power on all WAPs and monitoring the clients, nothing was making sense. I looked into the datasheet for each WAP model we had at this location and tried checking the calculations I made based on the information I was fed by our CWNE Network Architect and still something didn't make sense.

    I reached out to Ruckus support asking on how I can check the actual Tx Power on the WAP and that's when he hopped on and gave me access to the support shell to get the infomation I need.

    This is when I found out that the actual data provided by Ruckus on theor datasheets, doesnt really match what you get from the Access Point, I was kind of shocked. Below are some of the values I obtained while doing my checks on the WAP, you can see what power level you get based on the select settings i had at the time.

    ##### H550

    ```bash
    2.4GHz Max 17
    5GHz Max 19

    2.4GHz -5dB = 11 dBm
    5GHz   -2   = 17 dBm
    ```
    
    ![alt text](/Knowledge_Base/images/Ruckus_WAP_image-4.png)

    ##### R350
    
    ```bash
    2.4GHz Max 20  2 gain
    5GHz Max 20 gain 3
    Min is Zero
    
    10 -10 2.4Ghz
    14 -6 5Ghz
    ```

    ![alt text](/Knowledge_Base/images/Ruckus_WAP_image-2.png)

    ![alt text](/Knowledge_Base/images/Ruckus_WAP_image-3.png)

    ![alt text](/Knowledge_Base/images/Ruckus_WAP_image-5.png)

    ##### T350c
    
    ```bash
    2.4Ghz 23dBm
    5Ghz 22dBm
    ```

    ##### T310c
    
    ```bash
    2.4Ghz 20dBm
    5Ghz 22dBm 
    ```

    below is an example of what I used to script the WAPs on the SmartZone

    ```shell
    enable
    config
    ap 10:F0:68:11:7E:A0
    radio 2.4g channel 6
    radio 2.4 tx-power -6
    radio 5g channel 40
    radio 5g tx-power max
    exit
    yes

    ap 10:F0:68:11:69:00
    radio 2.4g channel 6
    radio 2.4 tx-power -10
    radio 5g channel 44
    radio 5g tx-power -6
    exit
    yes
    ```

    below is an example of turning off overrides on WAP, removing any changes made on WAP level for Tx Power and Channelization

    ```bash
    config
    ap 70:47:77:15:48:90
    no radio 2.4g channelization
    yes
    no radio 5g channelization
    yes
    no radio 2.4g tx-power
    yes
    no radio 5g tx-power
    yes
    end
    yes
    ```

!!! info ""

    Looks for
    2.4GHZ TX POWER TARGET > MCS0 HT20 > Pout dBm Value that's the Max
    5GHZ TX POWER TARGET > MCS0 VHT20 > Pout dBm Value that's the Max