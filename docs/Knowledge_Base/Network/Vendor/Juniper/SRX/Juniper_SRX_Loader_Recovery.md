!!! info ""

    Steps to recover from a Loader prompt **Loader>** ```can't load '/kernel' can't load '/kernel.old'```

    Press any key or space bar to enter into the loader prompt. < After pressing space bar or any key you would be directed to the below prompt > ```Loader >```

    **Recovery steps**

    1. Format a USB stick with the FAT32 file system.

    2. Copy the desired JunOS image (*.tgz) to the USB Stick. Make sure that no file(s) is there in the USB drive before copying the Junos image.
        https://support.juniper.net/support/downloads/?p=srx300
        
    3. Insert the USB stick into the USB port on the switch.

    4. Connect via console port to the switch.

    5. Power on the switch.

    6. Press the space bar after getting the above message to get into the loader prompt.

    7. Type the command ```loader> install file:///jinstall-ex-xxxx-xx.xxx.x-domestic-signed.tgz``` 
    - press [enter]
    - < Marked in BLUE is the Junos image file name copied in the USB>

    8. After the above command the switch would ```reboot``` and get you to the normal prompt.

    9.  It would ask for User Name to get in. Type ```root``` as username and ```press [enter]```, it would give you the ```% prompt```.
        - There is a possibility that system would not accept the root as username, this would be in the case of old units where root-login is denied.
        - Then there would be a need to recover the root password and there is a separate procedure for it.

    10. Above command (@ point 7 )will load the Junos in the switch but there is a possibility that switch may boot from the old partition having old version of image.

    11. Verify the same using # run show system snapshot media internal command. This command will show the Junos image present in both the partitions (In below image both have the same version).

    12. If the unit has the updated/desired verison then skip the step number **13**.

    13. Run command # run request system snapshot slice alternate to get the new version of Junos stored in alternate partition, in case required.

    14. Now the new unit is ready to join the VC or master.

    15. Make the connections and check the status of new unit . After this, the unit would get the configuration from master once joined in VC.
