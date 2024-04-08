!!! info "Recommended"
    
    Check release by using one of the following commands:
    
    ```bash
    lsb_release -a
    cat /etc/lsb-release
    cat /etc/os-release
    ```

    ```bash
    sudo apt clean
    sudo apt autoclean
    sudo apt update
    sudo apt upgrade -y
    sudo apt dist-upgrade
    sudo do-release-upgrade
    ```

    if needed

    ```bash
    apt list --upgradable
    ```

    
!!! warning "Upgrade using apt-fast - NOT TESTED"
  
    #Update your software sources 

    ```bash
    do-release-upgrade
    ```

    To point to the newer version of ubuntu. After it runs an update, and  asks you to press enter to start the process of upgrade.
    
    Open a new terminal, and start the upgrade, delete the lock file for apt first.
    
    ```bash
    sudo rm /var/lib/apt/lists/lock
    apt-fast dist-upgrade
    ```

    Remember that this has to be entered on a new terminal, because, if you cancel the upgrade at that step, the upgrade rolls back the changes to the repositories.
    
    After apt-fast finishes, you can shift to the original terminal and continue the upgrade
