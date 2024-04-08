!!! info ""

    ```bash
    lsusb -v
    dmesg | grep usbcore

    sudo apt install realtek-rtl88xxau-dkms
    sudo reboot
    ```

    Enabling monitor mode, assuming the adapter is named wlan0

    ```bash
    ifconfig wlan0 down
    airmon-ng check kill
    iwconfig wlan0 mode monitor
    ifconfig wlan0 up
    ```

    ```bash
    Chipset: Realtek RTL8812AU.
    Standards: IEEE 802.11 a/b/g/n/ac.
    Data Rate:

    802.11b: UP to 11Mbps.

    802.11g: UP to 54Mbps.

    802.11a: UP to 54Mbps.

    802.11n: UP to 150Mbps.

    802.11ac: UP to 867Mbps.
    Supported OS: Kali Linux (whether it is installed as a virtual machine or a main OS).
    Interface: USB 3.0.
    Antenna Type: 1 x 2.4Ghz RP-SMA connector.
    Antenna: 2x 5dBi Antennas.
    Frequency Range: 2.4 & 5 GHz.
    Security: WEP 64/128, 802.1X support, Wi-Fi Protected Access (WPA), WPA-PSK, WPA II-PSK.
    ```