!!! info ""

    ### Installing Mullvad VPN on Ubuntu Linux

    [Downloads | Mullvad VPN](https://mullvad.net/en/download/vpn/linux)

    
    #### Download the Mullvad signing key

    ```bash
    sudo curl -fsSLo /usr/share/keyrings/mullvad-keyring.asc https://repository.mullvad.net/deb/mullvad-keyring.asc
    ```

    #### Add the Mullvad repository server to apt

    ```bash
    echo "deb [signed-by=/usr/share/keyrings/mullvad-keyring.asc arch=$( dpkg --print-architecture )] https://repository.mullvad.net/deb/stable $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/mullvad.list
    ```

    #### Install the package

    ```bash
    sudo apt update
    sudo apt install -y mullvad-vpn
    ```

    #### configure Mullvad

    ```bash
    mullvad account login <account_number>
    mullvad lan set allow
    mullvad relay set location us
    mullvad connect
    mullvad lockdown-mode set on
    mullvad status
    ```

    #### Uninstall

    ```bash
    sudo apt purge mullvad-vpn
    ```
