!!! info ""

    ![alt text](/Knowledge_Base/images/heimdall_docker_-2.png)

    ![alt text](/Knowledge_Base/images/heimdall_docker_-1.png)

    heimdall docker yaml configuration file

    ```yaml
    ---
    version: "2.1"
    services:
    heimdall:
        /Knowledge_Base/images/heimdall_docker_: lscr.io/linuxserver/heimdall:latest
        container_name: heimdall
        environment:
        - PUID=1000
        - PGID=1000
        - TZ=America/New_York
        volumes:
        - /var/lib/docker/volumes/heimdall_data/_data:/config
        ports:
        - 7789:80
        - 7790:443
        restart: always
    ```

    ![alt text](/Knowledge_Base/images/heimdall_docker_1.png)

    **Sources**

    - [heimdall docker hub](https://hub.docker.com/r/linuxserver/heimdall)
