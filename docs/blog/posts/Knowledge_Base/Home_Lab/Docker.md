---
draft: false
date: 2024-06-16

---

!!! info ""

    ### Resource(s)

    - [docker manuals](https://docs.docker.com/manuals/)
    - [docker hub](https://hub.docker.com/)
    - [docker-OSX](https://github.com/sickcodes/Docker-OSX)


!!! info ""

    [docker official ubuntu](https://docs.docker.com/engine/install/ubuntu/)

    ### Installation

    #### Set up Docker's apt repository

    Add Docker's official GPG key

    ```bash
    sudo apt-get update
    sudo apt-get install ca-certificates curl
    sudo install -m 0755 -d /etc/apt/keyrings
    sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
    sudo chmod a+r /etc/apt/keyrings/docker.asc
    ```

    Add the repository to Apt sources:
    
    ```bash
    echo \
    "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
    $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
    sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt-get update
    ```

    #### Install the Docker packages

    ```bash
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    ```

    #### Verify the Installation

    Verify that the Docker Engine installation is successful by running the hello-world image

    ```bash
    sudo docker run hello-world
    ```

!!! info ""

    #### Create the docker group

    ```bash
    sudo groupadd docker
    ```

    #### Add your user to the docker group

    !!! Warning ""

        The docker group grants root-level privileges to the user. For details on how this impacts security in your system, see [Docker Daemon Attack Surface](https://docs.docker.com/engine/security/#docker-daemon-attack-surface).

    ```bash
    sudo usermod -aG docker $USER
    ```

    Log out and log back in so that your group membership is re-evaluated

    #### activate the changes to groups

    ```bash
    newgrp docker
    ```

    #### Verify that you can run docker commands without sudo

    ```bash
    docker run hello-world
    ```
    
    #### boot startup
    
    ##### To enable Docker start on boot

    ```bash
    sudo systemctl enable docker.service
    sudo systemctl enable containerd.service
    ```

    ##### To disable Docker start on boot

    ```bash
    sudo systemctl disable docker.service
    sudo systemctl disable containerd.service
    ```


    #### [Run the Docker daemon as a non-root user (Rootless mode)](https://docs.docker.com/engine/security/rootless/)


!!! info ""

    ### Docker compose plugin

    #### Install/Update the plugin only

    ```bash
    sudo apt-get update
    sudo apt-get install docker-compose-plugin
    ```

    Check the version

    ```bash
    docker compose version
    ```


!!! info ""

    ### cheatsheet

    #### Basic commands

    |command | description |
    |:-|:-|
    |```docker``` |To check all available Docker Commands|
    |```docker version``` |To show Docker version|
    |```docker info``` |Displays system wide information|
    |```docker pull``` |To pull the docker Images from Docker Hub Repository|
    |```docker build``` |To Docker Image from Dockerfile|
    |```docker run``` |Run a container from a docker|
    |```docker commit``` |To commit a changes in container file OR create newdocker Image|
    |```docker ps``` |List all the running containers. Add the flag to list all the containers. |
    |```docker start``` |To start a docker container |
    |```docker stop``` |To stop a docker container |
    |```docker logs``` |To view Logs for a Docker Container |
    |```docker rename``` |To rename Docker Container |
    |```docker rm``` |To remove the Docker Container, stop it first |

    #### Lifecycle commands

    |command | description |
    |:-|:-|
    |```docker create``` |Create a new container|
    |```docker run``` |Creates a docker container from docker image|
    |```docker pause``` |To pause a running container|
    |```docker unpause``` |To unpause a running container|
    |```docker stop``` |To stop a docker container|
    |```docker start``` |To start a docker container|
    |```docker Restart``` |To restart docker container |
    |```docker attach``` |Attach Terminal to Running container |
    |```docker wait``` |Block until one or more containers stop, then print their exit codes |
    |```docker rm``` |To remove the Docker Container, stop it first and then remove it |
    |```docker kill``` |To stop and remove Docker containers |

    #### Image commands

    |command | description |
    |:-|:-|
    |```docker build``` |To build Docker Image from Dockerfile|
    |```docker pull``` |To pull Docker Image from Docker Hub Registry|
    |```docker tag``` |To add Tag to Docker Image|
    |```docker images``` |To list Docker Images|
    |```docker push``` |To push Docker Images to|
    |```docker create``` |To show history of Docker Image|
    |```docker inspect``` |To show complete information in JSON format |
    |```docker save``` |To save an existing Docker Image |
    |```docker import``` |Create Docker Image from Tarball |
    |```docker export``` |To export existing Docker |
    |```docker load``` |To load Docker Image from file or archives |
    |```docker rmi``` |To remove docker images |

    #### Compose commands

    |command | description |
    |:-|:-|
    |```docker-compose build``` |To build docker compose file|
    |```docker-compose up``` |To run docker compose file - Create and start containers|
    |```docker-compose start``` |To start containers which are already created using docker compose file|
    |```docker docker-compose run``` |To run one one of application inside |
    |```docker-compose rm``` |To remove docker containers from docker compose |
    |```docker-compose ps``` |To check docker container status from docker compose |

    #### Networking commands

    |command | description |
    |:-|:-|
    |```docker network create``` |To create docker network|
    |```docker network ls``` |To list docker networks|
    |```docker network inspect``` |To view network configuration details |

    #### Prune commands

    |command | description |
    |:-|:-|
    |```docker system prune``` |To clean all resources which are dangling or not associated with any docker container|
    |```docker image prune``` |To remove Dangling Docker images|
    |```docker container prune``` |To remove all unused docker containers|
    |```docker volume prune``` |To remove all unused docker volumes |
    |```docker network prune``` |To remove all unused docker network |

    #### Container commands

    |command | description |
    |:-|:-|
    |```docker start``` |To start a Docker container|
    |```docker stop``` |To stop a running docker container|
    |```docker restart``` |To restart docker container|
    |```docker pause``` |To pause a running container|
    |```docker unpause``` |To unpause a running container|
    |```docker run``` |Creates a docker container from docker image|
    |```docker ps``` |To list Docker containers|
    |```docker exec``` |To Access the shell of Docker Container|
    |```docker logs``` |To view Logs for a Docker Container |
    |```docker rename``` |To rename Docker Containe |
    |```docker rm`` To remove Docker container |
    |```docker inspect``` |Docker container info command |
    |```docker attach``` |Attach Terminal to Running container |
    |```docker kill``` |To stop and remove Docker containers |
    |```docker cp``` |To copy files or folders between a container and from local filesystem. |

    #### Hub commands

    |command | description |
    |:-|:-|
    |```docker search``` |To search docker image|
    |```docker pull``` |To pull image from docker hub|
    |```docker login``` |To Log in to a Docker registry|
    |```docker push``` |Push an image or a repository to a registry |
    |```docker tag``` |Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE |
    |```docker logout``` |To logout from Docker Hub Registry |

    #### Logs and Monitoring commands

    |command | description |
    |:-|:-|
    |```docker ps -a``` |To show running and stopped containers|
    |```docker logs``` |To show Docker container logs|
    |```docker events``` |To get all events of docker container|
    |```docker top``` |To show running process in docker container |
    |```docker stats``` |To check cpu, memory and network I/O usage |
    |```docker port``` |To show docker containers public ports |




!!! info ""

    ### docker pentest container

    !!! info ""
    
        #### Install steps

        ```bash
        git clone --depth 1 https://github.com/aaaguirrep/pentest.git
        cd pentest
        docker build -t pentest .
        docker run --rm -it --name my-pentest pentest /bin/zsh
        ```


    !!! info ""

        #### Use cases

        Use the container to access HTB (Hack the Box) machines by HTB vpn
        
        ```bash
        docker run --rm -it --cap-add=NET_ADMIN --device=/dev/net/tun --sysctl net.ipv6.conf.all.disable_ipv6=0 --name my-pentest aaaguirrep/pentest /bin/zsh
        ```

        Share information from your local directory to container directory and save information on your local directory. You should save information under /pentest directory.

        ```bash
        docker run --rm -it -v /path/to/local/directory:/pentest --name my-pentest aaaguirrep/pentest /bin/zsh
        ```

        Expose internal container services (apache, squid) for your local environment

        ```bash
        docker run --rm -it --name my-pentest -p 80:80 -p 3128:3128 aaaguirrep/pentest /bin/zsh
        ```

        Inside the container start apache2 and squid services by the aliases

        ```bash
        apacheUp
        squidUp
        ```

        Mount directories by umount command

        ```bash
        docker run --rm -it --privileged --name my-pentest aaaguirrep/pentest /bin/zsh
        ```




