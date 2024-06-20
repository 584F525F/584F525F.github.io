!!! info ""

    [vsftpd appspot](https://security.appspot.com/vsftpd.html)

    ### vsftpd (very secure FTP daemon)

    #### Installing vsftpd

    ```bash
    sudo apt-get install -y vsftpd
    ```

    #### Update config to writable

    ```bash
    sudo nano /etc/vsftpd.conf
    ```

    locate `write_enable=YES` and remove the `#` in front of it and save the file changes.

    #Restart vsftpd

    ```bash
    sudo systemctl restart vsftpd
    ```

    Now you can FTP and do what you need to do.

    #### Uninstalling FTP

    To uninstall the package and remove all its configuration file, run the following

    ```bash
    sudo apt purge vsftpd
    ```
