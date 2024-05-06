!!! info ""

    ### Installation using docker compose

    This is the non root user method, which is a bit more secure than running as full root user, Yikes!

    ```bash
    #obtain your user PUID & GUID
    id 
    ```

    Navigate to a directory where you want to setup the docker image

    ```bash
    mkdir homepage
    cd homepage
    mkdir config
    mkdir images
    mkdir icons
    touch docker-compose.yaml
    nano docker-compose.yaml
    ```

    Paste the below configuration into the file, make sure you replace the $PUID & $PGID below with the ID number found above

    Save changes and exit the file once completed

    ```yaml
    ---
    services:
    homepage:
        image: ghcr.io/gethomepage/homepage:latest
        container_name: homepage-dashboard
        ports:
        - 3000:3000
        volumes:
        - ./config:/app/config # Make sure your local config directory exists
        - ./images:/app/public/images #incase you want to add custom images
        - ./icons:/app/public/icons #incase you want to add custom icons
        environment:
        PUID: $PUID
        PGID: $PGID
    restart: unless-stopped
    ```

    deploying the container

    ```bash
    compose up -d
    ```
    
    check docker container status

    ```bash
    docker ps
    ```

    You should now be able to access the dashboard at http://<ip_address>:3000

    You can check custom config here if you don't want to start from scratch [ChristianLempa Config](https://github.com/ChristianLempa/homelab/tree/main/homepage/homepage-prod-1/config)

!!! info ""

    ### Sources
    https://gethomepage.dev/latest/
