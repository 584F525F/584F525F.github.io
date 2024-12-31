!!! info ""

    This applies to Aruba Instant Access Points running Aruba InstantOS 3.3 or higher.

    ### How to troubleshoot configuration sync problems between master and slave IAPs?

    Configuration changes in an IAP cluster is centralized on Master IAP and it assigns a **cfg_id**(Configuration ID) to every different configuration change that occurred. If the Slave IAPs cfg_id is different with master, master should send recorded configuration to the slave Instant AP. On receiving configuration message from Master, Slave updates the configuration and then its own**cfg_id**.  
    
    Due to load or congestion on the network, configuration synchronization issues might rise up between Master and Slave IAPs. First steps in troubleshooting sync issues is to look at the config_id on Master and Slave.  
    
    Run the below command to view the config_id on Master or Slave IAP:  

    ![accsi_3](/Knowledge_Base/images/accsi_3.png)

    If the "current_config_id" on Master and Slave IAP equals, then both the IAPs are in Sync. But, if the "current_config_id" is different, then take the below steps to troubleshoot it further:

    - First, one need to understand if this issue is specific to a particular Slave IAP in the cluster or all other Slaves also have the similar issue. Therefore, login into other slave IAP and issue the same command i.e..  **"show delta-config".** 
    - If the issue exists with only one slave IAP then try to reboot so it can re-join the cluster and updates its configuration and the config_id. 
    - But, if the issue is with all the Slaves in the cluster, then check if the Master is creating a configuration message to push to all the Slaves, whenever a configuration change occurs. The command **"show delta-config <cfg_id>"**

    ![accsi_4](/Knowledge_Base/images/accsi_4.png)
    
    This indicates that the configuration packet is being created by Master to send to all the Slaves in the cluster.
    - Use the command **"show log system <count>"** to see if the config file is being sent on the network. 

    For example, below is a sample of the configuration change with reference to IAP clock

    ![accsi_5](/Knowledge_Base/images/accsi_5.png)

    **Note**: "Commit Apply"  saves the changes done from CLI
