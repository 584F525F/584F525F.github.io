
??? "METHOD 1 - Recommended"
    #### method 1 - Recommended
    run auto-clean
    ```bash
    sudo apt-get auto-clean
    ```

    fix file permission
    ```bash
    ls -al | grep resol
    drwxr-xr-x   5 root root     4096 Apr  9  2020 resolvconf
    lrwxrwxrwx   1 root root       29 Jan 22  2016 resolv.conf -> ../run/resolvconf/resolv.conf

    cd /etc
    sudo chmod 666 resolv.conf
    ```

    Check NetworkManager.conf
    ```bash
    sudo nano /etc/NetworkManager/NetworkManager.conf
    ```

    in main make sure dns is set to dhcp OR you can comment dns all together
    ```bash
    [main]
    dns=dhcp
    ```

    - This will tell the system to use the resolvconf service to automatically obtain the DNS server IPs.
    - It is also worth noting that, depending on your Linux distribution, the resolv.conf file may be a symbolic link to a file managed by the system, which is automatically updated with DNS server IPs obtained from DHCP. In this case, it's not necessary to make any changes to the resolv.conf file.
    ```bash
    sudo nano /etc/resolv.conf
    ```

    Replace the file content with the below
    ```
    # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
    #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
    # This file is managed by man:systemd-resolved(8). Do not edit.
    #
    # This is a dynamic resolv.conf file for connecting local clients to the
    # internal DNS stub resolver of systemd-resolved. This file lists all
    # configured search domains.
    #
    # Run "resolvectl status" to see details about the uplink DNS servers
    # currently in use.
    #
    # Third party programs must not access this file directly, but only through the
    # symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
    # replace this symlink by a static file or a different symlink.
    #
    # See man:systemd-resolved.service(8) for details about the supported modes of
    # operation for /etc/resolv.conf.

    nameserver 127.0.0.53
    ```
    
    TO RESTART - NEW WAY
    ```bash
    sudo systemctl restart NetworkManager
    ```

    TO RESTART - OLD WAY
    ```bash
    sudo service network-manager restart
    ```


??? "METHOD 2"
    #### method 2
    Add the resolved domains manually to /etc/hosts with this short script:
    ```bash
    resolveAptHosts()
    {
        mapfile -t hosts < <(
            sed -n -r '/^#/d; s;deb(-src)? (http://|ftp://)?([^/ ]+).*;\3;p'\
            /etc/apt/sources.list | sort | uniq )
        # delete all hosts from /etc/hosts, e.g., from an earlier call
        sudo sed -i -r '/^[0-9]{1,3}(\.[0-9]{1,3}){3}[ \t]+('"$( printf '|%s'\
            "${hosts[@]//./\\.}" | sed 's/^|//' )"')[ \t]*$/d' /etc/hosts
        for host in ${hosts[@]}; do
            ip=$( nslookup "$host" | sed -n -r 's|Address:[ \t]*([0-9.]+).*|\1|p' |
                tail -1 )
            sudo bash -c "echo $ip $host >> /etc/hosts"
        done
    }
    ```

    Now updating should work
    ```bash
    resolveAptHosts && sudo apt-get update
    ```

??? "METHOD 3"
    #### method 3
    Check DNS
    ```bash
    nmcli con show "Wired connection 1" | grep ipv4.dns
    ```

    Change your DNS
    ```bash
    sudo nmcli conn modify "Wired connection 1" ipv4.ignore-auto-dns yes
    sudo nmcli conn modify "Wired connection 1" ipv4.dns  "192.168.24.7 8.8.8.8"
    sudo systemctl restart NetworkManager
    ```

    Check if your host is being resolved
    ```bash
    nslookup google.com
    ```