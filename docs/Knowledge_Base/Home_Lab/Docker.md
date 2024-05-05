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

    ### docker pentest

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




