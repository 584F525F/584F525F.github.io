!!! success ""

    #### W: GPG error: [https://packagecloud.io/ookla/speedtest-cli/ubuntu](https://packagecloud.io/ookla/speedtest-cli/ubuntu) focal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8E61C2AB9A6D1557 E: The repository '[https://packagecloud.io/ookla/speedtest-cli/ubuntu](https://packagecloud.io/ookla/speedtest-cli/ubuntu) focal InRelease' is not signed.

    ```shell
    cd /etc/apt/sources.list.d
    sudo rm ookla_speedtest-cli.list
    sudo rm ookla_speedtest-cli.list.save
    sudo apt update && upgrade -y
    ```
