!!! info ""

    ##### Show hidden options

    ```shell
    ./john --list=hidden-options
    ```

    ##### Using session and restoring them

    ```shell
    ./john hashes --session=name
    ./john --restore=name
    ./john --session=allrules --wordlist=all.lst --rules mypasswd &
    ./john status
    ```

    ##### Show the potfile

    ```shell
    ./john hashes --pot=potFile --show
    ```

    ##### Search if a root/uid0 have been cracked

    ```shell
    john --show --users=0 mypasswdFile
    john --show --users=root mypasswdFile
    ```

    ##### List OpenCL devices and get their id

    ```shell
    ./john --list=opencl-devices
    ```

    ##### List format supported by OpenCL

    ```shell
    ./john --list=formats --format=opencl
    ```

    ##### Using multiples GPU

    ```shell
    ./john hashes --format:openclformat --wordlist:wordlist --rules:rules --dev=0,1 --fork=2
    ```

    ##### Using multiple CPU (eg. 4 cores)

    ```shell
    ./john hashes --wordlist:wordlist --rules:rules --dev=2 --fork=4
    ```
