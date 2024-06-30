!!! info ""
    
    [JUNOS Download](https://support.juniper.net/support/downloads/)
    
    !!! example ""
        
        #Before upgrading

        ```bash
        show version
        show chassis hardware | no-more
        show chassis environment | no-more
        show interface terse | no-more
        show configuration | no-more | display set
        ```
        
        Check system alarms and regarless of result run request
        
        ```bash
        show system alarms
        request system configuration rescue save
        request system autorecovery state save
        ```
        
        Check chassis alarms
        
        ```bash
        show  chassis  alarms
        show system storage partitions
        request system snapshot slice alternate
        show system snapshot media internal
        request system reboot
        show chassis alarms
        ```
        
        Make sure you have enough storage before upgrading /var
        
        ```bash
        show system storage | no-more
        ```
        
        If need more space, check files dry-run
        
        ```bash
        request system storage cleanup dry-run
        ```
        
        If all good to delete in results above, then run it. if not needed then ignore this step
        
        ```bash
        request system storage cleanup
        ```

        Enable services & Connect to SRX through FTP & upload firmware file to Juni, might need to update the security zone command, for zone name and interface

        ```bash
        configuration
        set system service telnet
        set system service ftp
        set security zones security-zone MGMT interfaces irb.1234 host-inbound-traffic system-services ftp
        commit
        ```
    

    !!! warning "You have 3 methods below, use only one!"
    
        **Method 1**: Upload the file into /var/tmp/ directory using filezilla or winscp and then check if you can see it
        
        ```bash
        run file list /var/tmp/
        request system software add /var/tmp/junos-srxsme-12.1X46-D40.2-domestic.tgz no-validate
        ```
        
        **Method 2**: FTP Method
        
        ```bash
        request system software add ftp://ftpuser:ftppass@172.16.1.1/junos-srxsme-12.1X46-D40.2-domestic.tgz no-copy no-validate
        ```
        
        **Method 3**: HTTPS Method
        
        ```bash
        file copy "https://cdn.juniper.net/software/junos/20.4R3.8/junos-srxsme-20.4R3.8.tgz?SM_USER=username@domainname.com&__gda__=1674734823_bd7351a3514eb61069sad8yoasd9" /var/tmp/junos-srxsme-20.4R3.8.tgz
        
        request system software validate /var/tmp/junos-srxsme-20.4R3.8.tgz
        
        request system software add /var/tmp/junos-srxsme-20.4R3.8.tgz no-validate
        ```

    !!! info ""
        
        Reboot after choosing your method
        
        ```bash
        request system reboot
        ```
        
        It can take 10-15 minutes before becoming available again, after it's back run the below
        
        ```bash
        show version
        show system boot-messages | no-more
        show chassis hardware | no-more
        show chassis environment | no-more
        show interface terse | no-more
        ```

        Check DHCP Leases
        
        ```bash
        show arp no-resolve
        ```

!!! info ""
    
    #### extra sources
    
    - [Junos Software Installation/Upgrade](https://supportportal.juniper.net/s/article/SRX-Getting-Started-Junos-Software-Installation-Upgrade?language=en_US)
    - [JUNOS OS Firmware Release Notes](https://www.juniper.net/documentation/product/us/en/srx300/#cat=release_notes&tab=release_20.4&sgroup=junos-os)
    - [JUNOS Download](https://support.juniper.net/support/downloads/)
    - [YT - Upgrade Software on Juniper SRX using WinSCP](https://www.youtube.com/watch?v=tYXv65VXP74)
