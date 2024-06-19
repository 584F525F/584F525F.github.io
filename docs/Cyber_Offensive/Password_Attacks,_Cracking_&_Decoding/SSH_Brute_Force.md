!!! info ""

    ### calc1f4r SSH-Bruteforcer

    [calc1f4r - Async SSH Bruteforce & Multi-threaded SSH bruteforcer](https://github.com/584F525F/SSH-Bruteforcer)

    #### Download repo & Install requirements

    ```bash
    git clone https://github.com/584F525F/SSH-Bruteforcer.git
    cd SSH-Bruteforcer/
    pip install requirements.txt -r
    ```

    #### Choose whether you want to use the async or multithread Python script and run the one you need

    !!! info ""
        
        ##### async

        ```bash
        usage: async-ssh-bruteforcer.py [-h] [-p PORT] -w WORDLIST -u USERNAME target

        positional arguments:
        target                Host to attack on e.g. 10.10.10.10.

        options:
        -h, --help            show this help message and exit
        -p PORT, --port PORT  Port to attack on, Default:22
        -w WORDLIST, --wordlist WORDLIST
        -u USERNAME, --username USERNAME
                                Username with which bruteforce to
        ```

        Example

        ```bash
        python3 async-ssh-bruteforcer.py -p <port> -u <username> -w <wordlist> <target>
        ```

    !!! info ""
        
        ##### multithreaded

        ```bash
        usage: multithreaded-ssh-bruteforcer.py [-h] [-p PORT] -w WORDLIST -u USERNAME [-t THREADS] target

        positional arguments:
        target                Host to attack on e.g. 10.10.10.10.

        options:
        -h, --help            show this help message and exit
        -p PORT, --port PORT  Port to attack on, Default:22
        -w WORDLIST, --wordlist WORDLIST
        -u USERNAME, --username USERNAME
                                Username with which bruteforce to
        -t THREADS, --threads THREADS
                                Specify the thread to use ,Default:4,supports 8 threads
        ```
        
        Example

        ```bash
        python3 multithreaded-ssh-bruteforcer.py -p <port> -u <username> -w <wordlist> -t <threads_default_4_supports_upto_8> <target>
        ```

!!! info ""

    ### k4yt3x orbitaldump

    [k4yt3x orbitaldump](https://github.com/k4yt3x/orbitaldump)

    You can install OrbitalDump through pip

    ```bash
    pip install -U --user orbitaldump
    orbitaldump
    ```

    Alternatively, you can clone this repository and run the source code directly

    ```bash
    git clone https://github.com/k4yt3x/orbitaldump.git
    cd orbitaldump
    python -m orbitaldump
    ```

    Usages

    ```bash
    A simple usage is shown below. This command below:
        t 10: launch 10 brute-forcing threads
        u usernames.txt: read usernames from usernames.txt (one username per line)
        p passwords.txt: read passwords from passwords.txt (one password per line)
        h example.com: set brute-forcing target to example.commands 
        -proxies: launch attacks over proxies from ProxyScrape
        python -m orbitaldump -t 2 -u usernames.txt -p passwords.txt -h example.com --proxies
    ```

