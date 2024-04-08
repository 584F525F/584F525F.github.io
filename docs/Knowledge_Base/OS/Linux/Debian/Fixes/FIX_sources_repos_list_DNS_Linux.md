!!! failure "Broken links"
    #### Locating the broken/trouble link when running apt update

    ```bash
    cd /etc/apt/
    #Replace BROKEN_LINK
    sudo grep -ir "BROKEN_LINK" .
    ```


!!! failure "/usr/lib/apt/methods/https could not be found"
    #### E: The method driver /usr/lib/apt/methods/https could not be found. N: Is the package apt-transport-https installed?

    ```bash
    cd /usr/lib/apt/methods
    sudo ln -s http https
    sudo apt install apt-transport-https
    sudo mv /var/lib/apt/lists /var/lib/apt/lists_backup
    sudo mkdir /var/lib/apt/lists
    sudo apt-get update
    ```

!!! failure ""
    #### E: The method driver /usr/lib/apt/methods/https could not be found.” error? Sounds like you may have added some https sources. Since there are no https sources in your sources.list, it would be something in /etc/apt/sources.list.d/.

    ```bash
    sudo apt install apt-transport-https ca-certificates
    ```

!!! failure ""
    #### GPG error: [https://packagecloud.io/ookla/speedtest-cli/ubuntu](https://packagecloud.io/ookla/speedtest-cli/ubuntu) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8E61C2AB9A6D1557

    ```bash
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8E61C2AB9A6D1557
    apt-key list
    ```

!!! failure ""
    #### Update errors

    ```bash
    sudo rm -r /var/cache/apt/archives/apt-fast
    sudo apt clean
    sudo apt auto-clean

    sudo mv /var/lib/apt/lists /var/lib/apt/lists_backup
    sudo mkdir /var/lib/apt/lists
    sudo apt-get update
    ```

!!! failure ""
    #### Failed to fetch https:// E: The repository 'https N: Updating from such a repository can't be done securely, and is therefore disabled by default. N: See apt-secure(8) manpage for repository creation and user configuration details.

    Locate the file in following path and remove the .list file

    ```bash
    sudo mv  /etc/apt/sources.list /etc/apt/sources.list.bak
    sudo mv  /etc/apt/sources.list.d /etc/apt/sources.list.d.bak
    sudo mkdir /etc/apt/sources.list
    sudo mkdir /etc/apt/sources.list.d

    /etc/apt/sources.list.d
    rm XXXX.list
    ```

!!! failure ""
    #### List update errors

    ```bash
    cd /etc/apt/sources.list.d
    ls -l

    sudo touch sources.list
    sudo nano sources.list

    ## ADD THE BELOW AND SAVE
    deb <http://security.debian.org/debian-security> jessie/updates main    
    deb <http://ftp.debian.org/debian/> jessie-updates contrib main   
    deb-src <http://security.debian.org/> jessie/updates contrib main  
    deb-src <http://ftp.debian.org/debian/> jessie-updates contrib main 

    sudo apt-get install apt-transport-https
    sudo apt-get update
    sudo apt-get upgrade

    cd /var/lib/apt/lists/

    cd /etc/apt/sources.list.d
    sudo nano sources.list
    ```
