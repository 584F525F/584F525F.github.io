!!! info ""

    To do a remote packet with Wireshark for Ruckus Access Point, you will need to SSH into the Master Access Point in order to run the following commands

    This sets up packet capture on 2.4GHz radio

    ```bash
    set capture wlan100 stream
    ```

    This displays status of 2.4GHz radio capture

    ```bash
    get capture wlan100 state
    ```

    To stop the capture on 2.4GHz radio

    ```bash
    set capture wlan100 idle
    ```

    This sets up packet capture on 5GHz radio

    ```bash
    set capture wlan101 stream
    ```

    This displays status of 5GHz radio capture

    ```bash
    get capture wlan101 state
    ```

    To stop the capture on 5GHz radio

    ```bash
    set capture wlan101 idle
    ```
