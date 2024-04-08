!!! success ""
    Proxychains
    
    ```bash
    sudo systemctl enable tor
    sudo service tor start
    sudo proxychains firefox
    ```

    Find low latency proxies https://spys.one/en/socks-proxy-list/
    
    ```bash
    sudo nano /etc/proxychains4.conf
    ```
    Also you can increase the number of chains
    Add proxies to end in this format socksx x.x.x.x yyyy
    
    ```bash
    round_robin_chain
    ```
