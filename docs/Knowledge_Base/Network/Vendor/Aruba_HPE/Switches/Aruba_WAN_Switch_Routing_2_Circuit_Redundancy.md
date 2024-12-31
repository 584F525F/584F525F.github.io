!!! info ""

    Example from Aruba Software revision  : WC.16.10.00030

    ```shell
    ip route 0.0.0.0 0.0.0.0 10.10.10.161 distance 20
    ip route 0.0.0.0 0.0.0.0 20.20.20.65
    ip route 20.20.20.0 255.255.255.240 10.10.10.161
    ip route 20.20.20.0 255.255.255.240 20.20.20.65
    ip routing

    vlan 100
    name "PrimaryISP"
    untagged 2-5,11-17,19-20,22-23
    ip address 20.20.20.78 255.255.255.240
    exit

    vlan 200
    name "SecondaryISP"
    untagged 6-7,9,18,21
    ip address 10.10.10.164 255.255.255.224
    exit
    ```
