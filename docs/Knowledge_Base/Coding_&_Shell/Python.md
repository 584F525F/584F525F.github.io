!!! info ""

    ### Python Extensions

    ```bash
    Docker
    IntelliCode
    Pylance
    Python Snippets 3
    Tabnine AI Autocomplete for Javascript, Python, Typescript, PHP, Go, Java, Ruby & more
    Test Adapter Converter
    Test Explorer UI
    ```

    ### Installing Python

    ```bash
    #Ubuntu 18.04, Ubuntu 20.04 and above
    #Python 3.8 doesn’t come by default on Ubuntu 18.04 and above, but it is available in the Universe repository. To install version 3.8
    sudo apt-get update
    sudo apt-get install python3.8 python3-pip
    #Linux Mint and Ubuntu 17 and below
    #Python 3.8 isn’t in the Universe repository, so you need to get it from a Personal Package Archive (PPA). For example, to install from the [“deadsnakes” PPA](https://launchpad.net/~deadsnakes/+archive/ubuntu/ppa)
    sudo add-apt-repository ppa:deadsnakes/ppa
    sudo apt-get update
    sudo apt-get install python3.8 python3-pip
    #You can run Python 3.8 with the python3.8 command and run pip with the pip3 command.
    ```

    ### orbitaldump - Python SSH Brute force

    ```bash
    pip install -U --user orbitaldump
    orbitaldump

    git clone https://github.com/k4yt3x/orbitaldump.git
    cd orbitaldump
    python -m orbitaldump

    Usages
    A simple usage is shown below. This command below:
        t 10: launch 10 brute-forcing threads
        u usernames.txt: read usernames from usernames.txt (one username per line)
        p passwords.txt: read passwords from passwords.txt (one password per line)
        h example.com: set brute-forcing target to example.commands 
        -proxies: launch attacks over proxies from ProxyScrape
        python -m orbitaldump -t 2 -u usernames.txt -p passwords.txt -h example.com --proxies
    ```

!!! info ""

    ### FTP Server

    (https://pypi.org/project/python-ftp-server/)

    ```python
    pip install python-ftp-server

    #Navigate to the folder you want to run FTP in
    python3 -m python_ftp_server

    #Once started, It will give you the port and login
    #Local address: ftp://<IP>:60000
    #User: <USER>
    #Password: <PASSWORD>

    #You can start service anonymous
    python3 -m python_ftp_server -u anonymous
    ```


!!! info ""

    ### HTTP Server

    This will run http file browser on port 8000, you can change the default port if needed.

    ```bash
    python -m http.server <port>
    python -m http.server 8443
    ```



