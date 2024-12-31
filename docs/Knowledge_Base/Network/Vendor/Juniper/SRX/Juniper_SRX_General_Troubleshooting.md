!!! info ""

    General Commands

    ```bash

    show chassis hardware
    Show chassis fpc pic-status
    show system alarms
    show chassis alarms
    show chassis environment
    show chassis hardware
    show chassis routing-engine
    show chassis forwarding-engine
    show chassis pic
    show system storage
    show system commit
    show pfe route > PFE Forwarding Table
    show system processes extensive | match "rpd|dcd|chassisd|pfed|snmpd|mdg"
    show version      >      package-prefix-arch-abi-release-edition.extension
    show log
    show log user
    show log messages
    show log accepted-traffic

    show security session flow

    show route
    show route forwarding-engine
    show route forwarding-table destination 192.168.10.100 
    show route table inet.0 192.168.10.100 extensive 
    show route table inet.0 192.168.10.0/24 


    file list > show directory
    file compare file <f1> <f1>
    file save 
    save > can be ftp, filename, path/filename
    load <merge, set, update, factory-default> terminal 
    file copy > to transfer files ftp or scp
    commit prepare > commit activate
    show | compare


    wildcard delete ...
    replace > move config from one place to another
    rename
    deactivate
    insert

    request system storage cleanup
    request system storage cleanup dryrun
    request system software add <path/image> validate no-copy  >> then restart
    request system snapshot
    request system configuration rescue save
    request system recover > create big image for recovery 1GB

    monitor interface
    monitor traffic > provides tcpdump


    *Password recovery*
    reboot 
    space bar
    boot + save
    recovery*set root password
    commit and exit
    reboot
    ```

!!! info ""

    Routing Troubleshooting

    ```bash

    show protocols
    show routing-options 	> Get Routing Types used & See what Policies are applied
    show routing-instances 	> Show Routing Instances protocols - Contains Interface Info
    show policy-options 	> policy-statement import export
    show firewall 			> Firewall filters and terms
    show security zones 	> Check Zone for irb
    show security policies 	> Permit & Deny Policy
    run show route hidden extensive


    $$Checklist for Verifying the BGP Protocol and Peers$$
    https://www.juniper.net/documentation/us/en/software/junos/bgp/topics/topic-map/troubleshooting-bgp-sessions.html


    **Verify BGP Peers

    show configuration												>	Verify BGP on a Border Router & Verify BGP on an Internal Router
    show route advertising-protocol bgp <neighbor-address> 			>	Verify That a Particular BGP Route Is Received on Your Router	| Look for (X active, 0 holddown, 0 hidden)	|	Use show configuration | match "neig"
    show route advertising-protocol bgp <neighbor-address>  detail	>	Verify That a Particular BGP Route Is Received on Your Router	| Look for (X active, 0 holddown, 0 hidden)	|	Use show configuration | match "neig"
    show route receive-protocol bgp <neighbor-address> 				>	Verify That a Particular BGP Route Is Received on Your Router	|	Use show configuration | match "neig"
    show policy-options policy-statement xxx						> 	If you have hidden or reject then use this
    run show route protocol bgp hidden <prefix> extensive			> 	Show hidden route
    show route <Hidden route address>								> 	Check if route is reachable

    **Examine BGP Routes and Route Selection
    show route destination-prefix < detail >	>	Examine the Local Preference Selection
    show route destination-prefix < detail >	>	Examine the Multiple Exit Discriminator Route Selection
    show route destination-prefix < detail >	>	Examine the EBGP over IBGP Selection
    show route destination-prefix < detail >	>	Examine the IGP Cost Selection
    show route forwarding-table					>	Examine Routes in the Forwarding Table

    ```
