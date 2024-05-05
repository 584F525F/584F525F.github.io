!!! info ""

    ### Esxi Backup

    [nakivo](https://www.nakivo.com/blog/back-up-and-restore-vmware-esxi-host-configuration-guide)


!!! info ""

    ### Clipboard copy & paste

    Power off VM

    ![](/Knowledge_Base/images/ESXI_098_.png)

    ![](/Knowledge_Base/images/ESXI_098_-1.png)

    Search for parameters and set value, if not there then create a new parameter.

    ```isolation.tools.copy.disable``` false
    ```isolation.tools.paste.disable``` false

    ![](/Knowledge_Base/images/ESXI_098_-2.png)


!!! info ""

    ### ESXI Dell custom bootable

    [how to create a bootable usb device with rufus to update dell servers](https://www.dell.com/support/kbdoc/en-us/000141551/how-to-create-a-bootable-usb-device-with-rufus-to-update-dell-servers)

    ```bash
    1-Download the tool to a Windows system
    2-Create a Smart Bootable ISO using the Dell Repository Manager (DRM)  or Download the matching ISO /Knowledge_Base/images/ESXI_098_ for the server you want to update from this list of repositories
    Start the tool
    Insert a USB device  (Rufus will auto-select if USB device)
    Choose the created or downloaded ISO-file  (Rufus will select the appropriate settings)

        Partition Screen = MBR
        File System = FAT32
        Cluster Size = 1024

    Click on Start to create the media
    Restart the server and boot from the created device
    ```


!!! info ""

    ### Esxi Patching & Upgrade

    Make sure to update the Volume, zip file name and -p image name

    ```bash
    esxcli software profile update -p ESXi-7.0U3g-20328353-standard -d /vmfs/volumes/62dcbea6-4709q3467-54da-c81f66ef4sdf/VMware-ESXi-7.0U3g-20328353-depot.zip --no-hardware-warning
    ```

    [https://customerconnect.vmware.com/patch](https://customerconnect.vmware.com/patch)

    ```bash
    esxcli software profile update -p ESXi-7.0U3k-21313628-standard -d /vmfs/volumes/62dcbea6-47095c67-er4a-c81f621dsf4d67/VMware-ESXi-7.0U3k-21313628-depot.zip --no-hardware-warning
    ```

!!! info ""

    ### Upgrade rollback

    [4sysops](https://4sysops.com/archives/roll-back-and-downgrade-vmware-esxi-version/)


!!! info ""

    ### Defragmenting and shrinking disks

    **Caution:** Do not shut down your virtual machine or the host machine while the disk is shrinking. In addition, do not try to cancel the process. Interrupting this process can cause irreparable damage to your virtual disk and you may not be able to start your virtual machine again.

    - 1- Remove snapshots for the VM >[all of them]
        
    - 2- OS Based steps
        
        - **Windows**
            
            To run a disk defragment within Windows, follow the instructions from Microsoft  
            - Windows XP [How to Defragment Your Disk Drive Volumes in Windows XP](http://support.microsoft.com/kb/314848)
            - Windows Vista [Improve performance by defragmenting your hard disk](https://support.microsoft.com/en-us/windows/ways-to-improve-your-computer-s-performance-c6018c78-0edd-a71a-7040-02267d68ea90)
            - Windows 7 [Improve performance by defragmenting your hard disk](https://support.microsoft.com/en-us/windows/ways-to-improve-your-computer-s-performance-c6018c78-0edd-a71a-7040-02267d68ea90)
            - Windows 8 [Improve performance by defragmenting your hard disk](https://support.microsoft.com/en-us/windows/ways-to-improve-your-computer-s-performance-c6018c78-0edd-a71a-7040-02267d68ea90)
            - Windows 10 [Improve performance by defragmenting your hard disk](https://support.microsoft.com/en-us/windows/ways-to-improve-your-computer-s-performance-c6018c78-0edd-a71a-7040-02267d68ea90)
    
            Shrinking the Virtual disk
            
            After defragmenting the virtual disk, use VMware Tools to erase empty disk sectors at the end of the disk to free the unused space.
                
            Double-click the VMware Tools icon in the system tray, or click **Start > Control Panel > VMware Tools > Click Shrink > Select Drive > Click Prepare to shrink**
                
            
        - **Linux**
            
            Ununtu defragment
                
            ```bash
            #no need to unmount disk
            sudo e4defrag -c /path/x/x/x

            #if you want to force it
            sudo e4defrag /path/x/x/x
            ```

            Shrinking the Virtual disk
            ```bash
            sudo vmware-toolbox-cmd disk shrinkonly
            ```





