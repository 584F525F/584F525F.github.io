!!! info ""


    ```bash
    sudo nmcli connection import type openvpn file mullvad_us_mia.conf
    #double check username and password before connecting
    nmcli connection up mullvad_us_mia
    nmcli conn show
    ```

