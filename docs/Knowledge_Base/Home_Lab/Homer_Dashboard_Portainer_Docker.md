!!! info ""

    ### Install Homer
    
    I keep all my dockers in a dockers folder in my home directory. If it doesn’t exist already, create this folder:-

    ```bash
    mkdir ~/dockers
    ```
    
    Now create a folder for Homer to live in.

    ```bash
    mkdir ~/docker/homer
    ```

    Create a folder for the assets

    ```bash
    mkdir ~/docker/homer/assets
    ```

    Change directory to this folder

    ```bash
    cd ~/docker/homer
    ```
    
    Create a docker-compose.yml file

    ```bash
    nano docker-compose.yml
    ```
    
    Paste the following. Change the 7500 part of 7500:8080 if you want it to listen on an alternative port to port 89.

    ```yaml
    ---
    version: "2"
    services:
    homer:
        image: b4bz/homer
        container_name: homer-home
        volumes:
        - ./assets/:/www/assets
        ports:
        - 7500:8080
        environment:
        - UID=1000
        - GID=1000
        restart: unless-stopped
    ```

    Save the file with ctl + x, then y to save

    Run the docker-compose file

    ```bash
    docker compose up -d
    ```

    1. Browse to the server IP and the port mentioned in the compose file, eg [http://1.1.1.1:89](http://1.1.1.1:89) and you should get the default dashboard.

![alt text](</Knowledge_Base/images/homer_1 3.png>)


!!! info ""

    ### Configuring Homer

    ```bash
    /home/app/docker/homer-home/assets
    sudo nano config.yml
    ```

    ```bash
    #Config for the Page sections and links
    sudo nano ./docker_prep/homer/data/config.yml

    #Icon placement
    ./docker_prep/homer/data/tools/

    ```

    ```yaml
    ---
    # Homepage configuration
    # See https://fontawesome.com/v5/search for icons options

    title: "Dashboard"
    subtitle: "Homer"
    logo: "logo.png"
    # icon: "fas fa-skull-crossbones" # Optional icon

    # Will load Dracula theme.
    stylesheet:
    - "assets/custom.css"

    header: true
    footer: ''

    # Optional theme customization
    theme: default
    colors:
    light:
        highlight-primary: "#3367d6"
        highlight-secondary: "#4285f4"
        highlight-hover: "#5a95f5"
        background: "#f5f5f5"
        card-background: "#ffffff"
        text: "#363636"
        text-header: "#ffffff"
        text-title: "#303030"
        text-subtitle: "#424242"
        card-shadow: rgba(0, 0, 0, 0.1)
        link: "#3273dc"
        link-hover: "#363636"
    dark:
        highlight-primary: "#3367d6"
        highlight-secondary: "#4285f4"
        highlight-hover: "#5a95f5"
        background: "#131313"
        card-background: "#2b2b2b"
        text: "#eaeaea"
        text-header: "#ffffff"
        text-title: "#fafafa"
        text-subtitle: "#f5f5f5"
        card-shadow: rgba(0, 0, 0, 0.4)
        link: "#3273dc"
        link-hover: "#ffdd57"

    # Optional message
    #message:
    #url: https://b4bz.io
    #style: "is-dark" # See https://bulma.io/documentation/components/message/#colors for styling options.
    #title: "Demo !"
    #icon: "fa fa-grin"
    #content: "This is a dummy homepage demo. <br /> Find more information on <a href='https://github.com/bastienwirtz/homer'>github.com/bastienwirtz/homer</a>"

    # Optional navbar
    links: [] # Allows for navbar (dark mode, layout, and search) without any links
    #links:
    #- name: "Contribute"
    #  icon: "fab fa-github"
    #  url: "https://github.com/bastienwirtz/homer"
    #  target: "_blank" # optional html a tag target attribute

    # Services
    # First level array represent a group.
    # Leave only a "items" key if not using group (group name, icon & tagstyle are optional, section separation will not be displayed).
    services:
    - name: "Home lab"
        icon: "fas fa-cloud"
        items:
        - name: "app"
            logo: "assets/tools/app.png"
            subtitle: "app"
            tag: "app"
            url: "https://172.16.0.17:9876"
            target: "_blank"
        - name: "app Local"
            logo: "assets/tools/app.png"
            subtitle: "app"
            tag: "app"
            url: "https://172.16.0.1:9876"
            target: "_blank"
        - name: "Docker app"
            logo: "assets/tools/app.png"
            subtitle: "cluster 2 app"
            tag: "app"
            url: "https://10.10.10.49:9443/#!/init/admin"
            target: "_blank"

    - name: "External Services"
        icon: "fas fa-cloud"
        items:
        - name: "app"
            logo: "assets/tools/app.png"
            subtitle: ""
            tag: "app"
            url: "https://dash.app.com/login"
            target: "_blank"
        - name: "app"
            logo: "assets/tools/app.png"
            subtitle: ""
            tag: "app"
            url: "https://app.com"
            target: "_blank"
    ```

!!! info ""

    ### Themes

    #### Dracula Theme

    [Homer - Dracula Theme](https://draculatheme.com/homer)

    ```dockerfile
    #Install using Git
    git clone https://github.com/dracula/homer.git
    ```

    #OR You can install it this way

    #Install manually
    #Download https://github.com/dracula/homer/archive/master.zip
    git clone https://github.com/dracula/homer/archive/master.zip

    **Activating theme**

    1- Copy custom.css to www/assets/custom.css.
    1- Copy dracula-background.png to www/assets/dracula-background.
    3- Put these lines into www/assets/config.yml and save the file, will load Dracula theme

    ```dockerfile
    stylesheet:
        - "assets/custom.css"
    ```

    4- Refresh the page. Boom! It's working.

