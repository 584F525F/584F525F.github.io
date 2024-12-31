!!! success ""

    #### Installing SSH Server and Enabling the service permanently

    ```bash
    sudo apt-get install ssh
    sudo service ssh start
    systemctl enable ssh.service
    ```

    #### Enable Kali Linux Remote SSH Service

    ```bash
    sudo update-rc.d -f ssh remove
    sudo update-rc.d -f ssh defaults
    ```

    #### Change Kali Default SSH Keys to Avoid MITM Attack

    ```bash
    sudo cd /etc/ssh/
    sudo mkdir default_kali_keys
    sudo mv ssh_host_* default_kali_keys/
    sudo dpkg-reconfigure openssh-server
    md5sum ssh_host_*
    cd default_kali_keys/
    sudo service ssh restart
    ```

    #### If you start getting warning signs when logging in

    ```bash
    nano /root/.ssh/known_hosts
    ```

    #### Change ssh port

    ```bash
    sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config_backup
    sudo nano /etc/ssh/sshd_config
    sudo service ssh restart
    ```

    #### Check SSH Status

    ```bash
    systemctl status ssh.service
    ```
