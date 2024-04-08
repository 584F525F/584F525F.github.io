!!! success ""
    #### #### ####  Kali - Login screen loop

    #### On login screen [CTRL+ALT+F1] to open shell
    Login with your creds

    ```shell
    sudo apt update && sudo apt upgrade -y
    ```

    #### Find which desktop environment you were using

    ```shell
    gdm3 -version or lightdm -v
    sudo apt-get clean
    ```

    #### Use the opposite one, the non-used environmet for install

    ```shell
    sudo apt-get install gdm3
    ```

    #### Proceed through setup windows

    ```shell
    dpkg-reconfigure gdm3
    sudo gdm3
    ```
    login now
