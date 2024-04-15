
To recover an Access Point whereby the management interface can no longer be accessed when in either "Unleashed Mode", Standalone or the AP is simple not functioning as expected and the ability to flash firmware via the controller is not working.

!!! info ""

    #### Pre-Requisites

    Download the latest version of standalone firmware relevant to your access point
    Please ensure you have installed a TFTP server running on your laptop or desktop which has access to the switch, for windows TFTPD32 is recommended and can be found > TFTPD32 Download  http://tftpd32.jounin.net/tftpd32_download.html
    
!!! info ""

    #### Configuring The Control Files

    Before you can tell the AP's to manually downgrade there firmware you must first create a file called fwcntrl.rcks and use your favourite text editor to modify the contents.

    The contents must contain the following:

    ```bash
    [rcks_fw.main]
    IP address of TFTP Host
    Standalone Firmware File Name
    Size of Standalone Firmware file in Bytes
    An example can be seen below, this file must be stored in your root TFTP directory along with the standalone firmware file.

    [rcks_fw.main]
    192.168.12.222
    H320_110.0.0.0.663.bl7
    12720124
    ```

!!! info ""

    ##### CLI Commands for AP's NOT running Unleashed 207.x & Later

    These commands must be ran on the AP directly via SSH once logged in

    ```bash
    fw set control fwcntrl.rcks
    fw set proto tftp
    fw set host 192.168.12.222 >>>> IP address of TFTP Server
    fw update
    ```

    Do not interupt the update once the command "fw update" has been entered. Should the update timeout re run the above commands.

!!! info ""

    ##### CLI Commands for AP's running Unleashed 207.x & Later

    These commands must be ran on the AP directly via SSH one logged in

    ```bash
    enable
    ap-mode
    fw set control fwcntrl.rcks
    fw set proto tftp
    fw set host 192.168.12.222 >>>> IP address of TFTP Server
    fw update
    ```

    Do not interupt the update once the command "fw update" has been entered. Should the update timeout re run the above commands.
