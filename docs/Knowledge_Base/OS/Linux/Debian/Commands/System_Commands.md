!!! info ""

    #### System OS timed reboot

    ```bash
    #IN 10 Minutes
    sudo shutdown -r +10
    
    #AT o'clock
    sudo shutdown –r 16:15
    
    #Cancel
    shutdown -c
    ```

!!! info ""

    #### enabling SSH

    ##### installing SSH

    ```bash
    sudo apt install openssh-server -y
    ```

    ![alt text](/Knowledge_Base/images/lx_sys_cmd_img-0.png)

    ##### check service status

    ```bash
    sudo systemctl status ssh
    ```

    ![alt text](/Knowledge_Base/images/lx_sys_cmd_img-1.png)

    #### ufw

    If you have ufw enabled, allow the connection on the SSH port by using the ufw command

    ```bash
    sudo ufw allow ssh
    ```

    ![alt text](/Knowledge_Base/images/lx_sys_cmd_img-2.png)

    enable and reload the ufw

    ```bash
    sudo ufw enable && sudo ufw reload
    ```

    ![alt text](/Knowledge_Base/images/lx_sys_cmd_img-3.png)
