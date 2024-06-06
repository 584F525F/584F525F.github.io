!!! info ""

    ### Requirements

    - Access to Junos OS Software and/or valid Juniper Account
    - Access to the SRX
    - Supported Models: **SRX300** / **SRX320** / **SRX340** / **SRX345** / **SRX380**


!!! info ""

    ### Common Upgrade Paths

    Build version is only applicable to the final upgrade. Intermediate versions can use any build version and as such the exact build version is omit from intermediate steps. For more information on software naming see `Naming Convention`. If you are upgrading an SRX and the upgrade path is not listed refer to `Upgrade Paths`.

    - From **15.1x49** to **19.4**
    - From **18.2** to **18.4** to **19.4**
    - From **19.4** to **20.4** to **21.4**
    - From **21.4** to **22.2**


!!! info ""

    ### Single SRX Upgrade

    For use with a single SRX device. For each software upgrade, this section should be completed in its entirety.

    !!! example ""

        #### Preparation

        ##### 1. Determine next Upgrade Version

        Log into the SRX using SSH.

        ```bash
        #gather the model and current software release
        show version
        ```
        Refer to the `Common Upgrade Paths` section to determine the next software version.

        ##### 2. Cleanup old files

        ```bash
        request system storage cleanup
        ```

        ##### 3. Update the Autorecovery State

        ```bash
        request system autorecovery state save
        ```

        ##### 4. Verify Alternate Root Partition Software

        ```bash
        show system software backup
        ```

        Verify the version listed matches the version from the previous step, **If they do not match** then run this command

        ```bash
        request system snapshot slice alternate
        ```

        <mark><mark>Note: This command will take some time to finish.</mark>
        
        ##### 5. Create a backup of the current configuration

        If copying the configuration directly from the terminal

        ```bash
        show configuration | display set
        ```

        If saving the configuration to a file for later transfer using your preferred file transfer method
        
        ```bash
        #replace “filename” with your desired name
        show configuration | display set | save /var/tmp/filename
        ```

        ##### 6. Download New Image

        If you already have the required software, this step can be skipped.

        Software downloads are available from Juniper here, search for the model and then select the version from the dropdown. If the version is not listed, you will need to open a support case with JTAC.

        Download the necessary version and log in with your Juniper account when prompted and accept the terms.

        After accepting terms you will be prompted with two options, select download image to localhost.


    !!! example ""

        #### Upgrade Procedure

        ##### 1. Upload the new version to the SRX

        Although multiple methods can be used to upload the new software to the device, this example will show the procedure using SCP.

        ```bash
        #SCP command
        scp path/to/local/filename  username@<SRX IP Address>:/var/tmp/
        ```

        The local path to the file will need to match your system however the target will always be “/var/tmp”.

        As an example, when running the SCP command from the same directory as the local file and uploading the image to an SRX on the IP address 1.2.3.4

        ```bash
        scp junos-srxsme-21.4R3.15.tgz jsmith@1.2.3.4:/var/tmp/
        ```

        <mark>Note: The extension is required otherwise the file will fail to upload.</mark>

        ##### 2. Validate and add the software package

        From the SRX command line, validate and add the software

        ```bash
        #modify the “filename” to match filename used in the previous step
        request system software add /var/tmp/filename
        ```

        This command will take some time to finish.

        To finish the install, reboot the device

        ```bash
        request system reboot
        ```

        A reboot will take roughly 15 to 25 minutes to complete. Do not power down the device during this time attempting to troubleshoot prematurely.

        ##### 3. Verification

        When the SRX has finished rebooting and is accessible again, log in and verify the expected version has been installed
        
        ```bash
        show version
        ```

        If the version does not match the expected result, verify the version of software used to upgrade the system.

        ##### 4. Rollback

        If a software upgrade causes an unforeseen issue, the system can be reverted using the commands:

        ```bash
        request system software rollback
        request system reboot
        ```


!!! info ""

    ### Cluster SRX Upgrade

    For use with an SRX cluster. For each software upgrade, this section should be completed in its entirety.

    Not all required changes can be completed from a single cluster node and as such, access to the other node is required. You can access the other node from the primary using
    
    ```bash
    #replace the “#” with the node you wish to access
    request routing-engine login node #

    #If a command is required to be run separately on both nodes, it will be indicated
    ```

    !!! example ""

        #### Preparation

        ##### 1. Verify Cluster is Healthy

        Log into the SRX using SSH.

        ```bash
        #verify the following are true

        show chassis cluster status
        ```

        ```powershell
        Node 0 and Node 1 are listed under Redundancy Group 0
        For each Redundancy Group, one node is primary and the other is secondary
        For each Redundancy Group, priority for either node is not 0 or 255
        If any of the above are false, stop and correct the issue
        ```

        Software upgrades should only be performed on healthy clusters to prevent further issues.

        ##### 2. Determine next Upgrade Version

        Log into the firewall using SSH.

        ```bash
        #gather the model and current software release
        show version
        ```

        Refer to 'Common Upgrade Paths' section to determine the next software version.

        ##### 3. Cleanup old files

        ```bash
        request system storage cleanup
        ```       

        ##### 4. Update the Autorecovery State

        ```bash
        request system autorecovery state save` on both nodes
        ```

        ##### 5. Verify Alternate Root Partition Software

        ```bash
        show system software backup
        ```

        Verify the version listed matches the version from the previous step.

        Log into the other node using 

        ```bash
        # replace # with the node you want to log into

        request routing-engine login node #
        ```

        Repeat the same verification.

        If either node does not match run

        ```bash
        request system snapshot slice alternate
        ```

        <mark>Note: This command will take some time to finish.</mark>

        ##### 6. Create a backup of the current configuration

        If copying the configuration directly from the terminal

        ```bash
        show configuration | display set
        ```

        If saving the configuration to a file for later transfer using your preferred file transfer method, use the command

        ```bash
        #replace <filename> with your desired name

        show configuration | display set | save /var/tmp/<filename>
        ```

        ##### 7. Download New Image

        If you already have the required software, this step can be skipped.

        Software downloads are available from Juniper here, search for the model and then select the version from the dropdown. If the version is not listed, you will need to open a support case with JTAC.

        Download the necessary version and log in with your Juniper account when prompted and accept the terms.

        After accepting terms you will be prompted with two options, select download image to localhost.


    !!! example ""

        #### Upgrade Procedure

        ##### 1. Upload the new version to the SRX Cluster

        Although multiple methods can be used to upload the new software to the device, this example will show the procedure using SCP.

        ```bash
        #SCP command
        scp path/to/local/filename  username@<SRX IP Address>:/var/tmp/
        ```

        The local path to the file will need to match your system however the target will always be `/var/tmp`.

        As an example, when running the SCP command from the same directory as the local file and uploading the image to an SRX on the IP address 1.2.3.4

        ```bash
        scp junos-srxsme-21.4R3.15.tgz jsmith@1.2.3.4:/var/tmp/
        ```

        <mark>Note: The extension is required otherwise the file will fail to upload.</mark>
        

        ##### 2. Copy software to the other node

        The software can be copied to the other node using 

        ```bash
        #replace “filename” with the name of the file from the previous step and “#” with the node number you are copying to.
        
        file copy /var/tmp/filename  node#:/var/tmp/
        ```      

        Verify the file has copied by logging into the other node and running

        ```bash
        file list /var/tmp/
        ```

        ##### 3. Validate and add the software package

        From the SRX command line, run the following to validate and add the software, modifying `filename` to match filename used in the previous step:

        ```bash
        request system software add /var/tmp/filename
        ```

        Repeat this command on the other node. This command will take some time to finish.

        To finish the install, reboot the devices

        ```bash
        request system reboot node all
        ```

        A reboot will take roughly 15 to 25 minutes to complete. Do not power down the devices during this time attempting to troubleshoot prematurely.

        ##### 4. Verification

        When the SRX has finished rebooting and is accessible again, log in and verify the expected version has been installed using `show version`.

        If the version does not match the expected result, verify the version of Software used to upgrade the system.

        Verify that the cluster has come back in a healthy state by running `show chassis cluster status` and verifying the following are true:

        ```powershell
        Node 0 and Node 1 are listed under Redundancy Group 0
        For each Redundancy Group, one node is primary and the other is secondary
        For each Redundancy Group, priority for either node is not 0 or 255
        ```
        
        <mark>Note: A cluster may take up to 15 minutes to resync after both devices are back online.</mark>

        ##### 5. Rollback

        If a software upgrade causes an unforeseen issue, the system can be reverted using the commands

        ```bash
        request system software rollback node all
        request system reboot node all
        ```
