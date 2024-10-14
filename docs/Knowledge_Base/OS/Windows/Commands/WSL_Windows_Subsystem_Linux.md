!!! info ""

    #### Enabling "WSL Windows Subsystem Linux"
    
    Run `cmd` as Admin

    ```bash
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all
    ```

    **Reboot**

    ```bash
    wsl --set-default-version 2

    wsl --install --distribution kali-linux
    #Setup the username and password
    ```

    #### Location to move files locally

    Change USER_PROFILE

    ```bash
    cd /mnt/c/users/USER_PROFILE/downloads
    ```

!!! info ""

    #### Reference(s)
    - Kali Linux WSL - [Kali wsl-preparations](https://www.kali.org/docs/wsl/wsl-preparations/#dism)
