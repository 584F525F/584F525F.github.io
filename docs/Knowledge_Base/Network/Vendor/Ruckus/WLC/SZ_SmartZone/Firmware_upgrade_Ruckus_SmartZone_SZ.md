!!! info ""

    #### Understanding the Firmware structure
    Each installed firmware will contain 3 parts and those are Control Plane, Data Plane & AP Firmware. If you install Firmware Version 5.2.2.0.317 that doesn't mean that the Firmware Version number below [Pointed in yellow] is the same version. Usually, the Firmware files hold different files with different versions that apply to different parts of the upgrade.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-49.png)

 
!!! info ""

    #### Checking Support Licenses
    It is crucial to follow this step as you will not be able to perform any sort of Firmware Upgrade without active support licenses for each Node included in the SmartZone upgrade.

    Navigate to **System** > **General Settings**

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-48.png)
    
    You must check how many SmartZones we have (Standalone/Cluster). In this example, I have 2 SmartZone Nodes.
    
    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-47.png)

    Navigate to **Administration** > **Licenses**
    
    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-46.png)

    Under **Installed Licenses**, you must have "SUP-Sxxx-PTNR" Licenses equal to the number of Nodes you found in the previous General Settings section. In our example, we have 2, which means I must see 2 Support Licenses for the same Node Names. The license must be active in order to perform an update. If expired you will not be able to upgrade the firmware.
    
    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-45.png)

    **Even if the numbers are correct, you must do the following steps:**

    1- Navigate to the next tab License Servers > Click Sync Now > Wait until you see a new entry in the table below with the current time and date and check if the results were successful. You will only have 1 result/row when running the sync in this tab.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-44.png)
    

    2- Navigate back to the Installed Licenses tab > Click Sync Now > You will need to wait a few seconds and maybe a minute, you MUST have as many results as you have Nodes. If you have 2 nodes then you must have two results and so on... 

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-43.png)

    In our example I had 2 Nodes, I see 2 results with the current date/time and with a successful result.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-42.png)
    

    3- Now you must check and confirm that you have an equal amount of licenses to the number of Nodes available in this Cluster and you must confirm that the Expiration Date is a future date and the license isn't expired.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-41.png)

    !!! warning ""
        
        Only if all the above checks out you can proceed with the next steps!


 
!!! info ""

    #### SmartZone Configuration Backup

    Log into SmartZone
    
    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-40.png)

    From the sidebar menu select Administration > Backup & Restore
    
    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-39.png)

    Under Cluster> Click Back Up Entire Cluster
    Note that some of these backups are big in size and can be over 2GB, this will possibly take a while and might be half an hour or more. Make sure when it's completed that you can find your recent backup in the Backups History
    
    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-38.png)

    Go to the next tab over Configuration Click Backup
    Now you will need to download that backup file, Click on the Newest dated backup entry you have and then click Download then attach it to your ticket.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-37.png)

 
!!! info ""

    #### Prepping for the upgrade procedure prior to the operation

    - Before jumping into the upgrade itself you will need to know what sort of SmartZone you're running and what the Controller Version is.
    - Navigate to **System** > **General Settings** > **Note the Controller Version**
    
    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-36.png)

    - Based on different SmartZone models the procedure might be different. Therefore you will need to navigate to [https://support.ruckuswireless.com/documents] in order to find the correct Guide to follow. In there look for the version you are upgrading to. You will need to download any Documents or Firmware.
    - Type in the search field "SmartZone upgrade" and you then will need to find the Guide that works with the setup you're trying to upgrade. All upgrades have to be compliant with the DCD firmware max version unless there is an exception approved by MOD.
    
    !!! danger ""

        Your upgrade path has to support the upgrade from the current Controller Version and also has to support the SmartZone Model. You also must make sure the new firmware supports all Acess Point models on-site by reading the upgrade Document for the Firmware version you're upgrading to.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-35.png)

    After downloading the document and finding the upgrade path needed, you will need to download the Firmware files from Ruckus and save them locally so they are ready for the upgrade when it's time.

    
!!! danger ""
    
    #### IMPORTANT!

    As per my many implementations and based on many discussions with Ruckus, keep in mind the following:

    - The SmartZone firmware and AP firmware are independent of each other, meaning that you should be able to upgrade the SmartZone and keep the APs on the old firmware and that won't affect the AP/Controller communications.
      - The reason why it's important to see what APs are supported is simply so you don't upgrade an AP zone with APs that won't be supported on the new target AP Firmware, so If you have multiple Zone, you can upgrade those that contain compatible firmware and leave the Zone with the target firmware isn't compatible with them.
      - Because of the previous scenario (Which contains a Zone with some unsupported APs) try to do the following:
        - Find the MAX firmware version that supports that Zone APs (Of course keeping in mind what your final target firmware is an upgrade path).
        - If the final target firmware is newer than that firmware then make sure your upgrade path will work. if it works then upgrade SZ to that firmware and then upgrade the Zone(s) with those AP to that firmware, then you can continue with the upgrade path and not upgrade Zones that contain APs that are not supported by that firmware. (Reason, why do this, is simply to have the latest applicable firmware onto those APs).
    
    !!! example ""

        Example

        You can see when I go to SZ 6.1.0 Upgrade I will be able to check the Versions you can upgrade from onto this firmware version, as well as the Supported platforms.

        You can hit the download tech document to review the detailed steps to do the upgrade.

        ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-34.png)

    !!! danger ""

        After you established the firmware needed, you will need to search for that firmware version in [Ruckus Firmware Download] 
        
        IMPORTANT MUST READ!!!
        
        After you locate it pay attention to further actions that might need to be implemented prior to the actual firmware upgrade. Read the release notes here and confirm all Access Points are supported. if you see like the one below where it says you need to update something, make sure you read the release notes for that link as well as it might be specific to the Access Point model or something else.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-33.png)

 
!!! danger ""
    IT IS YOUR RESPONSIBILITY TO READ THE OFFICIAL UPGRADE GUIDE AND RELEASE NOTES AS THEY MIGHT CONTAIN CRITICAL INFORMATION SPECIFIC TO EACH RELEASE! IF YOU IGNORE THIS STEP YOU MIGHT BREAK THE CONTROLLER AND RENDER THE SITE WITH NO WLAN CONTROLLER! 

 
!!! info ""

    #### The upgrade, action time!

    ##### SmartZone Firmware Upgrade Steps

    Once you have the firmware needed you will navigate to 

    **Administration** > **Upgrade** > **Upgrade** tab > click **Browse** > choose **file** > Click **Upload**

    !!! danger ""
        
        IMPORTANT!
        
        While the file is being uploaded you will need to click in between the tabs (Upgrade & Upgrade History) every few minutes to avoid upload timeout.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-32.png)

    At some point, you might receive this popup, Click Yes

    If you get to the below figure then click Upgrade if you have already taken a backup if you didn't take a backup then click Backup & Upgrade. If you didn't receive this then continue to the next figure.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-31.png)

    Click Yes

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-30.png)

    Click Yes

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-29.png)

    Wait while the operation is being performed, instead of just looking at GUI which might freeze. You can CLI into the SZ and run the commands below every few minutes to check the upgrade state.

    ```bash
    enable
    show upgrade-state
    ```

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-28.png)
    
    **Web GUI Upgrade state...**

    If at any time you feel a certain step is stuck then duplicate the web page and see if something would change.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-27.png)

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-26.png)

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-23.png)

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-25.png)

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-24.png)

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-22.png)

    Log into the SZ and confirm if the current version is the one you upgraded to, below is an example.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-21.png)
    
    !!! danger ""
        #### IMPORTANT!!!

        If this is a cluster, then you need to wait for all Nodes to apply the firmware. Usually, during the upgrade, you will see an Indicator for each Cluster Node with its progress.

        ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-20.png)

    The Master node will push that firmware and the upgrade is done one by one so this might take a while. Once you regain access to GUI, you can check on the Cluster Firmware Version by navigating to System > Cluster
    
    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-19.png)

    You will need to click on each Cluster Node and check the next figure.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-18.png)

    For Each Node that you click on. it will show its Information under Summary. Make sure all Nodes are on the New Firmware before proceeding with the next steps.

    This will show you the Control Plane Software Version which won't be the same as the Installed Firmware but it's a part of it.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-17.png)


    ##### Installing Signature Packs [Sigpack] / Application Control
    You only need to do this if required, usually, you will see a mention of it on the Firmware download page. For example: When I go to download SZ 5.2.2 Firmware, It was mentioned there that before upgrading to that Firmware version, I would need to update the SigPack.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-16.png)


    **To update the Sigpack, follow the below steps:**

    Navigate to Services & Profiles
    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-15.png)

    Click Signature Package > Browse > Upload
    Wait until the package is uploaded and applied. You will not get a confirmation that it is completed and it will only take a few seconds to update.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-14.png)

    Confirm the package File name / Version has been updated, you're done with this.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-13.png)

    
!!! info ""

    ##### AP Firmware Upgrade Steps

    Now you need to upgrade the Firmware on the APs, you can do that by following the below steps:

    For each Zone, you will need to click on the Zone and then click the More option

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-12.png)

    Click **Change AP Firmware**

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-11.png)

    Click **Upgrade**

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-10.png)

    Click **Yes**

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-9.png)

    If you receive a warning saying the below, continue with the upgrade.

    ```bash
    Upgrade to R5.2.2 does not support data migration (statistics, events, administrator logs). Existing system and network configuration are preserved. For further details download the 5.2.2 Release Notes before upgrading to prevent data loss
    Click OK
    ```

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-8.png)

    Now all the APs will reboot twice. Once for the Firmware upgrade and another to grab their configuration, to monitor the APs who adopted the firmware you can Navigate to **Access points** > **Access points** > and check the APs in each Zone.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-7.png)

    If you do not see the column AP Firmware then Click on the Wheel

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-6.png)

    Select **AP Firmware** and Click **OK**.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-5.png)

    In order to see updated results, you will have to click on the refresh button and you can sort by clicking the AP Firmware to see what's on new or old firmware until all is completed.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-4.png)

!!! info ""

    ##### Backup After the upgrade Steps

    Now that we have completed the upgrade you need to take both Cluster and Configuration backup on the new firmware.

    Navigate to Administration > Backup & Restore

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-3.png)

    Cluster Tab > Click Back Up Entire Cluster and wait until it's completed. You should see the new dates entry when completed.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-2.png)

    Configuration Tab > Click Backup and wait until it's completed. You should see the new dates entry when completed.

    ![alt text](/Knowledge_Base/images/SZ_SmartZone_image-1.png)

 
!!! info ""

    #### Troubleshooting

    - If for some reason you encountered some issues with the upgrade, go back - to the Firmware Upgrade Guide located at (Ruckus Support)[https://support.ruckuswireless.- com/documents] and look for the section named [Before Upgrading to This - Release]. This section might include some important TSB (Technical service - bulletin) information.
    - ![alt text](/Knowledge_Base/images/SZ_SmartZone_image.png)
    - For issues that require rolling back, read the [Rolling Back to a Previous - Software Version] section.
    - In the release notes located on the firmware download page, you will find - information about known issues and Workarounds under the section [Known - Issues].
    - You can call Ruckus TAC for assistance with any problems 855 782 5871
