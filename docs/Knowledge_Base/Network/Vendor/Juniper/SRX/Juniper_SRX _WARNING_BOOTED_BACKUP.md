!!! info ""

    #### 1. Problem

    SRX Firewalls running Junos Release 10.4R3, or later, have added resiliency based on the "resilient dual-root partition", which if the switch detects a corruption on the primary root le system, it boots from the alternate root partition.

    When this occurs, you are noticed in two ways: Alarm and Warning Banner


    ##### 1.1.  Alarm

    The following alarm message is generated

    ```bash
    show  chassis  alarms
    ```

    output

    ```bash
    1  alarms  currently  active Alarm  time  Class  Description

    2011-02-17  05:48:49  PST  Minor  Host  0  Boot  from  backup  root
    ```

    ##### 1.2. Warning

    ![srx_Warning_1](/Knowledge_Base/images/srx_Warning_1.png)


!!! info ""

    #### 2. Cause & Solution

    It likely became corrupted due to a sudden power loss, or ungraceful shutdown of the system.
    
    Repairing the primary partition when it is corrupted:

    - When the primary partition detects a corrupt, the device boots from the backup partition; which then becomes the active partition. Remember that after every
    successive reboot, the system will try to reboot from the current active partition.
    - You can repair the primary partition, without any downtime. No reboot is required after running the following commands. However the Alarm and Banner will be
    displayed.

    **Note:** As long as both of the partitions are healthy, there is no issue with running the switch on either of them. You only have to ensure that both the partitions are healthy, so that fail over can be done transparently between the
    two partitions, in case of any le corruption.


    ##### 2.1. Verification

    To verify if the primary partition is rebuilt, the same commands also inform about which partition is the current active partition.

    ```bash
    show system storage partitions
    ```

    output

    ```bash
    root> show system storage partitions
    fpc0:
    --------------------------------------------------------------------------
    Boot Media: internal (da0)
    Active Partition: da0s1a
    Backup Partition: da0s2a <-- this is the backup slice
    Currently booted from: backup (da0s2a) <-- shows booted from that slice
    Partitions information:
    Partition Size Mountpoint
    s1a 184M altroot
    s2a 184M /
    s3d 369M /var/tmp
    s3e 123M /var
    s4d 62M /config
    s4e unused (backup config) 
    ```

!!! info ""

    #### 3.Recovery Procedure

    ##### 3.1. Copy JUNOS Image From Backup

    Copy the Junos image from the backup partition to the primary partition, by using the following snapshot command For SRX

    ```bash
    request system snapshot slice alternate
    ```

    You will see the following message as the media is copied over

    ```bash
    Formatting alternate root (/dev/da0s2a)...
    Copying '/dev/da0s1a' to '/dev/da0s2a' .. (this may take a few minutes)
    The following filesystems were archived: /
    Note: This step ensures that you have consistent images on both the primary and backup partitions. This operation can take 5 to 10 minutes to complete.
    ```

    ##### 3.2. Verify Partitions

    The above command ensures that the alternate partition is repaired, without requiring a reboot. You can verify both the partitions by using the following command

    ```bash
    show system snapshot media internal
    ```

    This will show the time/date stamp for both partitions, which should show the current date/time on the (primary) partition which has been restored. See sample

    output

    ```bash
    root@srx> show system snapshot media internal
    Information for snapshot on internal (/dev/da0s1a) (primary)
    Creation date: Jan 22 23:48:47 2016 <-- Displays current date/time of operation in step 3.1
    JUNOS version on snapshot:
    junos : 12.1X44-D15.5-domestic
    Information for snapshot on internal (/dev/da0s2a) (backup)
    Creation date: Jan 1 06:08:27 2000
    JUNOS version on snapshot:
    junos : 12.1X44-D15.5-domestic
    ```

!!! info ""

    #### 4.Reboot

    In order to get rid of the alarm and ensure the partition has been repaired successfully, the system must be rebooted. There are 2 options to reboot given the environment the system is deployed in.

    ##### 4.1. Reboot Now

    If there is no risk to the network or customer, the system can be rebooted immediately. To get rid of the above alarm, use the following command to ensure that the switch boots from the primary partition:

    request system reboot
    The system, after the above command is executed, will reboot from the primary partition. The alarm or the warning message will no longer be displayed

    ##### 4.2. Reboot Later

    Reboot after X amount of minutes. Change the value after "in" to be the amount of minutes to reach the maintenance window scheduled. In this scenario, the system would reboot in 8 hours from the time the command is issued (60 minutes x 8 hours = 480)

    ```bash
    request system reboot in 480
    ```

    #### 5. Verify

    Once the system has rebooted, run the following commands to ensure the system has booted back to the primary partition

    ```bash
    show chassis alarms
    ```

    You should no longer see the alarm

    ```bash
    1 alarms currently active
    Alarm time Class Description
    2011-02-17 05:48:49 PST Minor Host 0 Boot from backup root 
    ```
