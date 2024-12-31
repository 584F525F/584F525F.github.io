!!! info ""

    Ubuntu Linux HTTPS Inspection

    #### Method 1

    ```bash
    sudo apt install mitmproxy
    export MITMPROXY_SSLKEYLOGFILE=/tmp/logfile.txt
    echo $MITMPROXY_SSLKEYLOGFILE

    mitmproxy

    ```

    Open browser and navigate to [mitm.it](http://mitm.it)

    #### Method 2

    ```bash
    export SSLKEYLOGFILE=/home/odroid/Desktop/ssllogfile.txt
    echo $SSLKEYLOGFILE

    firefox &

    sudo wireshark
    ```
