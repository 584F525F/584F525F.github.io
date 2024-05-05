!!! info ""

    ### Install

    You must have Docker installed prior to installing Portainer

    create the volume that Portainer Server will use to store its database

    ```bash
    docker volume create portainer_data
    ```

    install portainer CE

    ```bash
    docker run -d -p 8000:8000 -p 8443:8443 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ee:latest
    ```

    check to see whether the Portainer Server container has started

    ```bash
    docker ps
    ```

    Log in https://localhost:9443
    
    Sources: [Docker Linux Install CE](https://docs.portainer.io/start/install-ce/server/docker/linux)


!!! info ""

    ### Upgrade

    ```
    docker ps -a

    #Locate the ones with name "/portainer"
    #0eab77c40087   portainer/portainer-ce      "/portainer"
    #take first 4 chars of the random string

    docker stop 0eab
    docker rm 0eab

    docker pull portainer/portainer-ce:latest

    docker run -d -p 8000:8000 -p 8443:8443 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ee:latest
    ```

!!! info ""

    ### Upgrade Docker Compose v1 to v2

    ```bash
    docker compose up -d
    ```

    Update your package repositories and install docker-compose-plugin

    ```bash
    sudo apt update
    sudo apt install docker-compose-plugin
    ```

    Check the installation succeeded by retrieving Docker Compose’s version

    ```bash
    docker compose version
    Docker Compose version v2.3.3
    ```

    Now you can remove Docker Compose v1, unless you want to retain it to provide compatibility with legacy scripts. Both docker-compose (v1) and docker compose (v2) can co-exist if you need them to. If you’re removing v1, it’s normally found as a single binary at /usr/local/bin/docker-compose

    ```bash
    sudo rm /usr/local/bin/docker-compose
    ```

    You could now set up a shell alias to redirect docker-compose to docker compose. This would let you keep using scripts that expect Compose v1, using your new v2 installation

    ```bash
    echo 'alias docker-compose="docker compose"' >> ~/.bashrc
    source ~/.bashrc
    docker-compose version
    Docker Compose version v2.3.3
    ```

    You’re now ready to start managing your containers with Compose v2


!!! info ""

    ### Watcher - WatchTower (Auto docker container updates)

    #### Deploy Watchtower

    ```bash
    docker run --name watchtower -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower
    ```

    #### Run Watchtower in debug mode

    You might wonder why there is no log output apart from the welcome message. If you want to increase the logging level or watchtower, you simply just add an argument.

    ```bash
    docker run --name watchtower -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower --debug
    ```

    #### Run Watchtower only once, in debug mode

    ```bash
    docker run --name watchtower -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower --run-once --debug
    ```

    #### Exclude Container from Watchtower

    ```bash
    docker run -d --label=com.centurylinklabs.watchtower.enable= false nginx
    ```

    #### Scheduled Updates and clean up old images

    ```bash
    docker run --name watchtower -v /var/run/docker.sock:/var/run/docker.sock --restart unless-stopped containrrr/watchtower --schedule "0 0 4 * * *" --debug --cleanup
    ```
