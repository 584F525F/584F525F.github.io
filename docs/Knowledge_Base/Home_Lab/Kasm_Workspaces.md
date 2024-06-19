!!! info ""

    ### Resources
    - [https://kasmweb.com/](https://kasmweb.com/)
    - [https://kasmweb.com/docs/latest/admin_guide.html](https://kasmweb.com/docs/latest/admin_guide.html)
    - [https://kasmweb.com/docs/latest/install/system_requirements.html](https://kasmweb.com/docs/latest/install/system_requirements.html)
    - [https://github.com/kasmtech/KasmVNC](https://github.com/kasmtech/KasmVNC)
    - [Single Server Upgrade](https://kasmweb.com/docs/latest/upgrade/single_server_upgrade.html)
    - [KASM port change](https://kasmweb.com/docs/latest/how_to/port_change.html#change-port-post-installation)


!!! info ""

    ### Installation

    #### Creating A Swap Partition

    - Swap should be approximately 1gb per concurrent session you expect to run at any given time. Please adjust according to your needs.
    - Default is 1g.
    
    This below is running with 10g, which runs 10 concurrent sessions.
    
    ```bash
    sudo fallocate -l 10g /mnt/10GiB.swap
    sudo chmod 600 /mnt/10GiB.swap
    sudo mkswap /mnt/10GiB.swap
    sudo swapon /mnt/10GiB.swap
    ```

    #### Verify swap file exists

    ```bash
    cat /proc/swaps
    ```

    #### To make the swap file available on boot

    ```bash
    echo '/mnt/4GiB.swap swap swap defaults 0 0' | sudo tee -a /etc/fstab
    ```

    #### Install

    From this link you can obtain the Standard Install command which should contain the updated Kasm release.
    [Single Server Installation — Kasm 1.14.0 documentation](https://kasmweb.com/docs/latest/index.html)

    ```bash
    cd /tmp
    curl -O https://kasm-static-content.s3.amazonaws.com/KASM_release_1.14.0.3a7abb.tar.gz
    tar -xf KASM_release_1.14.0.3a7abb.tar.gz

    #If you want to install on default port 443 then run this command.
    #If you want to install with non default port, check the next step
    sudo bash KASM_release/install.sh -L 443
    ```

    If you want to install with non default port then change the port number below 8443 to the desired port number.

    ```bash
    sudo bash KASM_release/install.sh -L 8443
    ```

    Log into the Web Application running on port 443 at **https://<WEBAPP_SERVER>**

    The Default usernames are admin@kasm.local and user@kasm.local.
    **The passwords will be randomly generated and presented at the end of the install unless the `--admin-password` or/and `--user-password` are specified.**


!!! info ""

    ### Workspaces and registry

    ![](/Knowledge_Base/images/KASM_image-8.png)

    Search for registries on github [Repository search results · GitHub](https://github.com/search?q=in%3Areadme+sort%3Aupdated+-user%3Akasmtech+%22KASM-REGISTRY-DISCOVERY-IDENTIFIER%22&type=repositories)

    ![](/Knowledge_Base/images/KASM_image-9.png)

!!! info ""

    ### Kasm Cert Install

    ```bash
    #Stop the Kasm Services
    sudo /opt/kasm/bin/stop

    #backup and then replace kasm_nginx.crt & kasm_nginx.key file
    sudo cp /opt/kasm/current/certs/kasm_nginx.crt /opt/kasm/current/certs/kasm_nginx_backup.crt
    sudo cp /opt/kasm/current/certs/kasm_nginx.key /opt/kasm/current/certs/kasm_nginx_backup.key
    ls /opt/kasm/current/certs
    #Insert value crt
    nano /tmp/kasm_nginx_new.crt
    #insert value key
    nano /tmp/kasm_nginx_new.key
    sudo cp /tmp/kasm_nginx_new.crt /opt/kasm/current/certs/kasm_nginx.crt
    sudo cp /tmp/kasm_nginx_new.key /opt/kasm/current/certs/kasm_nginx.key
    rm /tmp/kasm_nginx_new.crt
    rm /tmp/kasm_nginx_new.key

    #Start the Kasm Services
    sudo /opt/kasm/bin/start

    #Test if nginx is running correctly. Wait 30 seconds
    sudo docker ps | grep kasm_proxy

    sudo cp /opt/kasm/current/certs/KASM_nginx_backup.crt /opt/kasm/current/certs/KASM_nginx.crt
    sudo cp /opt/kasm/current/certs/KASM_nginx_backup.key /opt/kasm/current/certs/KASM_nginx.key
    ```

!!! info ""

    ### 

    ![](/Knowledge_Base/images/KASM_image.png)

    ![](/Knowledge_Base/images/KASM_image-1.png)

    ![](/Knowledge_Base/images/KASM_image-2.png)

    ![](/Knowledge_Base/images/KASM_image-3.png)

    ![](/Knowledge_Base/images/KASM_image-4.png)

    ![](/Knowledge_Base/images/KASM_image-5.png)

    ![](/Knowledge_Base/images/KASM_image-6.png)

    ![](/Knowledge_Base/images/KASM_image-7.png)




!!! info ""

    ### Uninstalling Kasm

    Stop All Kasm services

    ``` bash
    sudo /opt/kasm/current/bin/stop
    ```

    Remove any Kasm session containers

    ``` bash
    sudo docker rm -f **$(**sudo docker container ls -qa --filter="label=kasm.kasmid"**)**
    ```

    Remove Kasm service containers

    ``` bash
    export KASM_UID=**$(**id kasm -u**)**export KASM_GID=**$(**id kasm -g**)**
    sudo -E docker compose -f /opt/kasm/current/docker/docker-compose.yaml rm
    ```

    Remove the Kasm docker network

    ``` bash
    sudo docker network rm kasm_default_network
    ```

    Remove the Kasm database docker volume

    ``` bash
    sudo docker volume rm <docker_image>
    ```

    Remove the Kasm docker_image

    ``` bash
    sudo docker rmi redis:5-alpine
    sudo docker rmi postgres:9.5-alpine
    sudo docker rmi kasmweb/nginx:latest
    sudo docker rmi kasmweb/share:1.12.0
    sudo docker rmi kasmweb/agent:1.12.0
    sudo docker rmi kasmweb/manager:1.12.0
    sudo docker rmi kasmweb/api:1.12.0

    sudo docker rmi $(sudo docker images --filter "label=com.kasmweb.image=true" -q)
    ```

    Remove the Kasm installation directory structure

    ``` bash
    sudo rm -rf /opt/kasm/
    ```
    Remove the Kasm User Accounts

    ``` bash
    sudo deluser KASM_db
    sudo deluser kasm
    ```
    Restart

    ``` bash
    sudo /opt/kasm/current/bin/stop
    sudo /opt/kasm/current/bin/start
    ```


!!! info ""

    ### Kasm change port after install

    Below is example to change from 443 to 8443
    
    
    Stop All Kasm services

    ```bash
    sudo /opt/kasm/current/bin/stop
    ```

    Update the agent.app.config.yaml with the desired port

    ```bash
    sudo sed -i "s/public_port.*/public_port: 8443/g" /opt/kasm/current/conf/app/agent.app.config.yaml
    ```

    (Optional) Verify the changes with the following command

    ```bash
    sudo grep public_port /opt/kasm/current/conf/app/agent.app.config.yaml
    public_port: 8443
    public_port: 8443
    ```

    Update the Kasm Nginx proxy configuration to listen on the desired port

    ```bash
    sudo sed -i "s/listen.*/listen 8443 ssl ;/g" /opt/kasm/current/conf/nginx/orchestrator.conf
    ```

    (Optional) Verify the changes with the following command

    ```bash
    sudo grep listen /opt/kasm/current/conf/nginx/orchestrator.conf
    listen 8443 ssl ;
    ```

    Update the docker-compose.yaml to export the desired port for kasm_proxy container

    ```bash
    sudo sed -i "s/- \"443:443\"/- \"8443:8443\"/g"  /opt/kasm/current/docker/docker-compose.yaml
    ```

    (Optional) Verify the changes with the following command

    ```bash
    sudo grep kasm_proxy -A5 /opt/kasm/current/docker/docker-compose.yaml
    container_name: KASM_proxy
    KASM_image: "kasmweb/nginx:latest"
    ports:
        - "8443:8443"
    networks:
        - KASM_default_network
    ```

    Remove the KASM_proxy container so it can be recreated using the updated port mapping

    ```bash
    sudo docker rm -f KASM_proxy
    ```

    Start All Kasm services

    ```bash
    sudo /opt/kasm/current/bin/start
    ```




!!! info ""

    ### Kasm Docker

    [Default Docker Images](https://kasmweb.com/docs/latest/guide/custom_/Knowledge_Base/images/KASM_images.html)

    If you want to manually pull the docker_images to Kasm Workspaces

    ```bash
    sudo docker pull docker <docker_image>

    #You will need to change the version numbers
    sudo docker pull kasmweb/firefox:1.14.0
    sudo docker pull kasmweb/fedora-38-desktop:1.14.0
    sudo docker pull kasmweb/alpine-318-desktop:1.14.0
    sudo docker pull kasmweb/kali-rolling-desktop:1.14.0
    sudo docker pull kasmweb/core-kali-rolling:1.14.0
    sudo docker pull kasmweb/qbittorrent:1.14.0
    sudo docker pull kasmweb/tor-browser:1.14.0
    sudo docker pull kasmweb/sublime-text:1.14.0
    sudo docker pull kasmweb/ubuntu-jammy-dind:1.14.0
    sudo docker pull kasmweb/postman:1.14.0
    sudo docker pull kasmweb/remmina:1.14.0
    sudo docker pull kasmweb/remnux-focal-desktop:1.14.0
    sudo docker pull kasmweb/core-parrotos-5:1.14.0
    sudo docker pull kasmweb/libre-office:1.14.0
    sudo docker pull kasmweb/telegram:1.14.0
    sudo docker pull kasmweb/pinta:1.14.0
    sudo docker pull kasmweb/filezilla:1.14.0
    ```

!!! info ""

    ### Cleaning old & unused Images

    ```bash
    sudo docker image ls
    sudo docker image prune -a
    ```


!!! info ""

    ### Changing MAX Concurrent Docker Pulls

    Stop the Agent Services

    ```bash
    sudo /opt/kasm/bin/stop
    ```

    Replace the value of `max_concurrent_docker_pulls` in the agent config with the new value

    ```bash
    sudo vi /opt/kasm/current/conf/app/agent.app.config.yaml
    ```

    Start the Agent Services

    ```bash
    sudo /opt/kasm/bin/start
    ```

    If you tail the logs of the agent, after 30 seconds, and if you have multiple images pending will see notifications of images now being pulled

    ```bash
    sudo docker logs -f kasm_agent
    ```

    Kasm stop start

!!! info ""

    ### Troubleshooting

    [Troubleshooting — Kasm 1.14.0 documentation](https://kasmweb.com/docs/latest/guide/troubleshooting.html#server-side-issues)
