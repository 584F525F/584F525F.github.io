!!! info ""

    [calc1f4r - Async SSH Bruteforce & Multi-threaded SSH bruteforcer](https://github.com/584F525F/SSH-Bruteforcer)

    #### Download repo & Install requirements

    ```bash
    git clone https://github.com/584F525F/SSH-Bruteforcer.git
    cd SSH-Bruteforcer/
    pip install requirements.txt -r
    ```

    #### Choose whether you want to use the async or multithread Python script and run the one you need

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

    ```bash
    python3 async-ssh-bruteforcer.py -p <port> -u <username> -w <wordlist> <target>
    ```

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

    ```bash
    python3 multithreaded-ssh-bruteforcer.py -p <port> -u <username> -w <wordlist> -t <threads_default_4_supports_upto_8> <target>
    ```
