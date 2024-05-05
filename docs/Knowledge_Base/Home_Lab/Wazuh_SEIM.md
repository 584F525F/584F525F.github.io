!!! info ""

    ### Add the Wazuh repository

    Install the GPG key:
    
    ```bash
    curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | gpg --no-default-keyring --keyring gnupg-ring:/usr/share/keyrings/wazuh.gpg --import && chmod 644 /usr/share/keyrings/wazuh.gpg
    ```

    Add the repository
    
    ```bash
    echo "deb [signed-by=/usr/share/keyrings/wazuh.gpg] https://packages.wazuh.com/4.x/apt/ stable main" | tee -a /etc/apt/sources.list.d/wazuh.list
    ```

    Update the package information

    ```bash
    apt-get update
    ```

    For Debian 7, 8, and Ubuntu 14 systems import the GCP key and add the Wazuh repository (steps 1 and 2)

    ```bash
    apt-get install gnupg apt-transport-https
    curl -s https://packages.wazuh.com/key/GPG-KEY-WAZUH | apt-key add -
    echo "deb https://packages.wazuh.com/4.x/apt/ stable main" | tee -a /etc/apt/sources.list.d/wazuh.list
    ```

!!! info ""

    ### Deploy a Wazuh agent 

    To deploy the Wazuh agent on your endpoint, select your package manager and edit the `WAZUH_MANAGER` variable to contain your Wazuh manager IP address or hostname.
    
    ```bash
    WAZUH_MANAGER="10.10.10.49" apt-get install wazuh-agent
    ```

    If needed for additional deployment options such as agent name, agent group, and registration password [Deployment variables for Linux - Deployment variables](https://documentation.wazuh.com/current/user-manual/deployment-variables/deployment-variables-linux.html)

    Enable and start the Wazuh agent service

    ```bash
    systemctl daemon-reload
    systemctl enable wazuh-agent
    systemctl start wazuh-agent
    ```

    The deployment process is now complete, and the Wazuh agent is successfully running on your Linux system.

    !!! warning ""
        **Recommended action** - Disable Wazuh updates Compatibility between the Wazuh agent and the Wazuh manager is guaranteed when the Wazuh manager version is later than or equal to that of the Wazuh agent. Therefore, we recommend disabling the Wazuh repository to prevent accidental upgrades. To do so, use the following command
    
    ```bash
    sed -i "s/^deb/#deb/" /etc/apt/sources.list.d/wazuh.list
    apt-get update

    #Alternatively, you can set the package state to `hold`. This action stops updates but you can still upgrade it manually using `apt-get install`.

    echo "wazuh-agent hold" | dpkg --set-selections
    ```

!!! info ""

    ### Uninstall a Wazuh agent

    To uninstall the agent, run the following commands:

    Remove the Wazuh agent installation.

    ```bash
    apt-get remove wazuh-agent

    #Some files are marked as configuration files. Due to this designation, the package manager does not remove these files from the filesystem. If you want to completely remove all files, run the following command:

    apt-get remove --purge wazuh-agent
    ```

    Disable the Wazuh agent service
    
    ```bash
    systemctl disable wazuh-agent
    systemctl daemon-reload
    ```

!!! info ""

    ### Resources
    
    [Deploying Wazuh agents on Linux endpoints - Wazuh agent](https://documentation.wazuh.com/current/installation-guide/wazuh-agent/wazuh-agent-package-linux.html)


!!! info ""

    ### Wazuh Server Installation

    OVA [Virtual Machine (OVA) - Installation alternatives](https://documentation.wazuh.com/current/deployment-options/virtual-machine/virtual-machine.html)

    Docker [Deployment on Docker - Installation alternatives · Wazuh documentation](https://documentation.wazuh.com/current/deployment-options/docker/index.html)


    #### OVA Installation 
    After installing the OVA, go into SSH to change the passwords for all services
    ```bash
    curl -so wazuh-passwords-tool.sh https://packages.wazuh.com/4.4/wazuh-passwords-tool.sh
    #-ap is the password for shell wazuh-user
    sudo bash wazuh-passwords-tool.sh -a -au wazuh -ap wazuh

    #### Restart the server afterwards

    ```
    
    !!! warning ""
        WARNING: Wazuh indexer passwords changed. Remember to update the password in the Wazuh dashboard and Filebeat nodes if necessary, and restart the services. hope it helps anyone struggling.


    #### Restarting Wazuh services

    ```bash
    sudo systemctl restart wazuh-manager
    sudo systemctl restart wazuh-indexer
    sudo systemctl restart wazuh-dashboard
    sudo systemctl restart filebeat
    ```


