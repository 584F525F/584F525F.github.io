!!! info ""

    #### Stop the automatic updater

    choose not to download and install updates

    ```bash
    sudo dpkg-reconfigure -plow unattended-upgrades

    reboot.
    ```

    #### Make sure any packages in an unclean state are installed correctly:

    ```bash
    sudo dpkg --configure -a
    ```

    #### Get your system up-to-date:

    ```bash
    sudo apt update && sudo apt -f install && sudo apt full-upgrade
    ```

    #### Turn the automatic updater back on, now that the blockage is cleared:

    ```bash
    sudo dpkg-reconfigure -plow unattended-upgrades
    ```

    Select the package unattended-upgrades again.
