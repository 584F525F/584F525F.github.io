#### System OS timed reboot
    ```bash
    #IN 10 Minutes
    sudo shutdown -r +10
    
    #AT o'clock
    sudo shutdown –r 16:15
    
    #Cancel
    shutdown -c
    ```

#### enabling SSH
??? ""

    ##### installing SSH
    ```bash
    sudo apt install openssh-server -y
    ```

    ##### check service status
    ```bash
    sudo systemctl status ssh
    ```

    #### ufw
    If you have ufw enabled, allow the connection on the SSH port by using the ufw command
    ```bash
    sudo ufw allow ssh
    ```

    enable and reload the ufw
    ```bash
    sudo ufw enable && sudo ufw reload
    ```
