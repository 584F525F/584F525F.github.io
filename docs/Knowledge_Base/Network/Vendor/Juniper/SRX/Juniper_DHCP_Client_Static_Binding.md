!!! info ""

    Configuring a Client DHCP binding, you will need:

    - Client device IP Address
    - Client device MAC Address

    ```bash
    set access address-assignment pool <dhcp-pool-name> family inet host <host-name> hardware-address <mac-address : seperated>
    set access address-assignment pool <dhcp-pool-name> family inet host <host-name> ip-address <ip-address>
    ```

    Example

    ```bash
    set access address-assignment pool BackOfficeLAN family inet host StaffPC hardware-address 11:00:62:58:88:95
    set access address-assignment pool BackOfficeLAN family inet host StaffPC ip-address 192.168.1.20
    ```

    Checking on DHCP binding

    ```bash
    show dhcp server binding
    show dhcp server statistics
    ```
