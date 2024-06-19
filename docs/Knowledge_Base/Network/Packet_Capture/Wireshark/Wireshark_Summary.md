!!! info ""

    ### Resources

    - [Laura Chappel - Packet Capture samples](https://www.chappell-university.com/traces)
    - [Laura Chappel - Blog](https://www.chappell-university.com/lauras-lab)
    - [Wireshark User's Guide](https://www.wireshark.org/docs/wsug_html/)
    - [Chris Greer - Youtube](https://www.youtube.com/channel/UCHN1aYRP473xX6Z13H_mxMQ)
    - [Chris Greer - Udemy](https://www.udemy.com/course/wireshark-ultimate-hands-on-course/?couponCode=LEADERSALE24A)
    - [TryHackMe - Wireshark](https://tryhackme.com/module/wireshark)
    - [Packet Dissection](https://github.com/boundary/wireshark/blob/master/doc/README.dissector)


!!! info ""

    ### GEO_IP

    #### Step 0: Test Pcap

    Grab a trace file to test your GeoIP mapping setup [**gen2-mapping**](gen2-mapping.pcapng)

    #### Step 1: Download the GeoIP Database Files

    Visit [**geolite2**](https://dev.maxmind.com/geoip/geoip2/geolite2/) to get the latest GeoLite2 free database files.

    - _GeoLite2-City_[date].tar.gz_
    - _GeoLite2-Country_[date].tar.gz_
    - _GeoLite2-ASN_[date].tar.gz_

    The files contain a date stamp indicating the revision date of the file. MaxMind updates the GeoLite2 Country and City databases on the first Tuesday of each month and the GeoLite2 ASN database every Tuesday.

    ![](https://static.wixstatic.com/media/fe341d_82b19bdd5f8e4c96823b1e2cfaa7465c~mv2.png/v1/fill/w_740,h_210,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/fe341d_82b19bdd5f8e4c96823b1e2cfaa7465c~mv2.png)

    #### Step 2: Set Up a Directory and Extract Key .mmdb Files to this Directory

    **Create a directory** on your drive called _MaxMind_. This is where you will put all your .mmdb files after unzipping them.
    
    The MaxMind DB files you downloaded are in gzipped .tar file format. You'll need a tool to **unzip the files** (I use 7-Zip and WinZip on my systems).
    
    When you unzip the files, you will have these three files:
    - _GeoLite2-City_[date].tar_
    - _GeoLite2-Country_[date].tar_
    - _GeoLite2-ASN_[date].tar_
    
    Now the files are in .tar format (tarballs). We have one more unzipping process to go through. **Unzip each of these .tar files.** You will then have three directories containing the separate database files.

    - _\GeoLite2-City_[date]_ directory containing the _GeoLite2-City.mmdb_ file
    - _\GeoLite2-Country_[date]_ directory containing the _GeoLite2-Country.mmdb_ file
    - _\GeoLite2-ASN_[date]_ directory containing the _GeoLite2-ASN.mmdb_ file
    
    Finally, **copy each of the .mmdb files** from these directories into your \MaxMind directory.
    Your directory should look something like this

    ![](https://static.wixstatic.com/media/fe341d_b652d1087ba6437cbddbb58c3ed7eac8~mv2.png/v1/fill/w_740,h_173,al_c,lg_1,q_85,enc_auto/fe341d_b652d1087ba6437cbddbb58c3ed7eac8~mv2.png)

    #### Step 3: Add a Path in Wireshark Preferences

    !!! warning ""
        
        **_Note_**_: This setting is unlike most other Wireshark preference settings. When you set up GeoIP mapping in a profile, the setting actually saved in the Wireshark default profile directory. This makes the GeoIP mapping available in all profiles._
    
    In Wireshark, select **Edit | Preferences | Name Resolution**. Next to MaxMind database directories, click the **Edit** button. Click the + button to add a directory and navigate to your \MaxMind directory. Click OK to select your \MaxMind directory and click OK to close the Preferences window.
    
    **Restart Wireshark.**

    ![](https://static.wixstatic.com/media/fe341d_c47f9f6f5e72431fabb2541ff1dc7113~mv2.png/v1/fill/w_699,h_546,al_c,q_90,enc_auto/fe341d_c47f9f6f5e72431fabb2541ff1dc7113~mv2.png)

    #### Build Your Maps

    Now comes the cool stuff! Load a trace file in Wireshark and select **Statistics | Endpoints**. Click on either the **IPv4** or **IPv6** tabs to see if you have some City, Country, AS Number, and AS Organization information available. An example is shown below.
    ![](https://static.wixstatic.com/media/fe341d_51b65dccb5c748a79c842da7595a6d37~mv2.png/v1/fill/w_740,h_463,al_c,q_85,usm_0.66_1.00_0.01,enc_auto/fe341d_51b65dccb5c748a79c842da7595a6d37~mv2.png)
    Notice the Map button on the bottom of the Endpoints window. Click the **Map** button and select **Open in browser**. Wireshark launches your default browser and maps endponits based on the information available in the GeoLite2 database files. Pretty cool, eh?
    ![](https://static.wixstatic.com/media/fe341d_ba54020b0dd04473836a3fc04f16b855~mv2.png/v1/fill/w_634,h_413,al_c,lg_1,q_85,enc_auto/fe341d_ba54020b0dd04473836a3fc04f16b855~mv2.png)
    
    You can also right click on any Endpoint row and select Apply as filter, Prepare a filter, Find, or Colorize.

    #### Filter on GeoIP Information

    Here's another interesting thing you can do after setting up GeoIP mapping in Wireshark. Look inside the IPv4 or IPv6 headers of the packets.
    The GeoIP information is contained at the end of the IPv4/IPv6 header, as shown in the image below.
    
    ![](https://static.wixstatic.com/media/fe341d_a0b4fa982a444cef8cffe3b5e56d862c~mv2.png/v1/fill/w_740,h_928,al_c,q_90,usm_0.66_1.00_0.01,enc_auto/fe341d_a0b4fa982a444cef8cffe3b5e56d862c~mv2.png)
    You can create filters based on these fields. Some filter examples are shown below.
    - Destination City [IPv4]: ip.geoip.dst_city == "Dublin"
    - Source or Destination City [IPv4]: ip.geoip.city == "Dublin"
    - Destination Country: ip.geoip.dst_country == "Ireland"
    - Destination Country based on Country Code: ip.geoip.dst_country_iso == "IE"
    - All Destination Countries Except United States: !ip.geoip.country == "United States"
    
    Note that _ip_ must be replaced with _ipv6_ if you are working within an IPv6 header.

    #### Add and Sort GeoIP Columns
    
    Consider right-clicking on any of the GeoIP lines shown in the previous image and select **Apply as column**.

    ![](https://static.wixstatic.com/media/fe341d_06bc70be64cc44d19949ee13dd07da6f~mv2.png/v1/fill/w_740,h_553,al_c,q_90,usm_0.66_1.00_0.01,enc_auto/fe341d_06bc70be64cc44d19949ee13dd07da6f~mv2.png)
    

    #### Reources

    [Map IP Address Locations with Wireshark (Using GeoIP) - YouTube](https://youtu.be/IlVppluWTHw)
    [GeoIP Mapping in Wireshark](https://www.chappell-university.com/post/geoip-mapping-in-wireshark)


!!! info ""

    ### Dissectors

    [https://github.com/wireshark/wireshark/blob/master/epan/dissectors/packet-snmp.c](https://github.com/wireshark/wireshark/blob/master/epan/dissectors/packet-snmp.c)
    [https://github.com/wireshark/wireshark](https://github.com/wireshark/wireshark)
    [https://www.wireshark.org/docs/wsdg_html_chunked/ChDissectReassemble.html](https://www.wireshark.org/docs/wsdg_html_chunked/ChDissectReassemble.html)




