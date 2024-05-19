!!! info "Timeshift installation"
    
    ### Timeshift installation
    ```bash
    sudo apt install timeshift
    sudo timeshift --create --comments "A new backup" --tags D
    sudo timeshift --restore

    -tags D stands for Daily Backup
    -tags W stands for Weekly Backup
    -tags M stands for Monthly Backup
    -tags O stands for On-demand Backup
    ```

!!! info "Using Timeshift"

    ### Using Timeshift
    
    #### Installing TImeshift
    ```bash
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AB19BAC9
    sudo add-apt-repository -y ppa:teejee2008/ppa
    sudo apt-get update
    sudo apt install timeshift
    ```

    #### Creating a Restore point
    Now, launch your terminal and type the following command
    ```bash
    sudo timeshift --create --comments "first backup"
    Restore Point
    ```

    (Creating a restore point/snapshot may take several minutes, depends on the size of the files & your hardware resources)

    #### Writing a comment
    ```bash
    -- comments "A new backup"
    ```
    
    #### tags
    There are several tags, that specify what kind of backup it is. As an example
    -tags D stands for Daily Backup
    -tags W stands for Weekly Backup
    -tags M stands for Monthly Backup
    -tags O stands for On-demand Backup (default option)

    You can put any tag as your wish, after the comments
    
    #### Restoring a snapshot
    ```bash
    sudo timeshift --restore
    ```
    This command shows you a list of created snapshots & ask, from which snapshot you want to restore the system, you have to select the snapshot index to proceed further

    After that, press the Enter key to continue, when It asks about reinstalling the GRUB2 bootloader, press the 'y' key, then press the Enter key again & finally, press the 'y' key to start the system restore...

    At this moment, you have restored the system successfully, and the PC will take a reboot to ensure that your restoration is fully done.

    (**When your PC is in the restoring phase, don't do any work. It might interfere with the restoring process.)
