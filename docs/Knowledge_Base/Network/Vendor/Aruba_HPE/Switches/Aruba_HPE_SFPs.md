!!! info ""

    ## Aruba Optics

    [ArubaOS-Switch and ArubaOS-CX Transceiver Guide](https://www.arubanetworks.com/techdocs/Switches/xcvrs/5200-3362/index.html#Overview.html)

    In the search box located in the right corner > Type the switch model. For example, I want to find SFP for HP 2920 Switch. I will type 2920 and hit enter.

    ![Aruba_Optics_1](</Knowledge_Base/images/Aruba_Optics_1.png>)

    On the left side it will filter which parts of the document have information about the switch model you searched for. You will need to click on each on to load the results and at the same time you need to search the web page it self for that model number so you can locate the information inside each document.

    ![Aruba_Optics_2](</Knowledge_Base/images/Aruba_Optics_2.png>)

    I clicked the first link and you can see I did browser search and I see the result loaded. This page is for SFP+, if you don’t need SFP+ then click on the next option until you see what you want.

    The SKU is the part number that I would need to order if I want a specific type of transceiver, in this case it’s SFP+.!

    ![Aruba_Optics_3](</Knowledge_Base/images/Aruba_Optics_3.png>)

    I tried another document and in this one it’s for 1GB SFP Optical Transceiver, I can see the model there for browser search and then the available SKU (part number) that I can order.

    ![Aruba_Optics_4](</Knowledge_Base/images/Aruba_Optics_4.png>)

!!! info ""

    ## HP Optics

    [HPE Transceiver information](https://techhub.hpe.com/eginfolib/networking/docs/switches/WB/15-18/5998-8162_wb_2920_mcg/content/ch11s05.html)

    If replacing existing SFP
    
    ```bash
    Show interface transceiver
    ```
    
    ![HPE_Optics_1](/Knowledge_Base/images/HPE_Optics_1.png)

    If you want to specify the port show interface transceiver ethernet [Port-Number]
    
    ![HPE_Optics_2](/Knowledge_Base/images/HPE_Optics_2.png)

    You can also do show interface transceiver detail

    If you do not specify a port then you will see all results and you will need to find the ports you want to get SFP replacement for, this give you all the details you need, in this case Model Number for the SFP is what you need.

    ![HPE_Optics_3](/Knowledge_Base/images/HPE_Optics_3.png)
    
    Show interface transceiver ethernet [Port-Number] detail
    
    ![HPE_Optics_4](/Knowledge_Base/images/HPE_Optics_4.png)
