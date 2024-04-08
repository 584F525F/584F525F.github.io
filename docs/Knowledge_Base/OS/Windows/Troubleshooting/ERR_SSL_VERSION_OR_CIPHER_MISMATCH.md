Are you seeing error "_**ERR_SSL_VERSION_OR_CIPHER_MISMATCH**_" when trying to load a GUI for a piece of equipment? If so then follow the steps below and make the changes need to the browser you're using.

![alt text](<Pasted image 20231125004337.png>)


!!! info ""
    ## Microsoft Internet Explorer

    1. 1. Open Internet Explorer
        2. From the menu bar, click **Tools** >  **Internet Options** > **Advanced tab**
        3. Scroll down to Security category, manually **check** the option boxes for:
            - **Use TLS 1.0**
            - **Use TLS 1.1**
            - **Use TLS 1.2**  
                ![alt text](<Pasted image 20231125004427.png>)
        4. Click **OK**
        5. Close your browser and **restart Internet Explorer**

!!! info ""
    ## Google Chrome

    Below steps might not work for you, based on newer update you might not be able to locate advanced options.

    1. Open Google Chrome
    2. In the address bar, type **chrome://settings/**
    3. Scroll down and select Show **advanced settings**...
    4. Scroll down to the **Network section** and click on **Change proxy settings**...
    5. Select the **Advanced tab**
    6. Scroll down to **Security category**, manually **check** the option boxes for Use **TLS 1.0, Use TLS 1.1 and Use TLS 1.2**
    7. ![alt text](<Pasted image 20231125004444.png>)
    8. Click **OK**
    9. Close your browser and **restart Google Chrome**

!!! info ""
    ## Mozilla Firefox

    1. Open Firefox
    2. In the address bar, type **about:config** and press Enter
    3. In the Search field, enter **tls**. Find and double-click the entry for **security.tls.version.min**
    4. Set the integer value to **1**  ![alt text](<Pasted image 20231125004504.png>)
    5. Click **OK**
    6. Close your browser and **restart Mozilla Firefox**

!!! info ""
    ## Opera

    1. Open Opera
    2. Click Ctrl plus **F12**
    3. Select the **Advanced Tab**
    4. Scroll down to the Security section and click on the **Security Protocols** Button
    5. Manually check the option boxes for  **Enable TLS 1,  Enable TLS 1.1 and Enable TLS 1.2**  
    ![alt text](<Pasted image 20231125004519.png>)
    6. Click **OK**
    7. Close your browser and **restart Opera**

!!! info ""
    ## Apple Safari

    > There are no options for enabling SSL protocols. If you are using Safari version 7 or greater, TLS 1.0, TLS 1.1 and TLS 1.2 are automatically enabled.
