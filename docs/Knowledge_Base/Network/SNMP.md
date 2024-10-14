!!! info ""

    #### SNMP set

    **SNMP set** allows you to make changes to device configuration using OID of the device's MIB, for instance, enabling telnet through SNMP.
    
    I use [ezfive SnmpSet.exe](https://ezfive.com/snmpsoft-tools/snmp-set/), you can download it and then open a `cmd` windows, navigate to the exe file location then call it and pass the values to it.
    
    Note that you cannot just copy pasta the below, you will need to change the values based on MIB/OID and host.

    ```bash
    snmpset.exe -r:192.168.1.10 -c:password -t:10  -tp:int -v:2c -o:.1.3.6.1.4.1.1234.1.1.2.1.32.0 -val:1
    ```

    #### Other tools

    If you get your hands on a MIB from whatever vendor, using something like [ireasoning MIB Browser](https://www.ireasoning.com/mibbrowser.shtml) might help you dig down into the OIDs and understand their values, description and data types.

    Other useful tools [SnmpGet](https://ezfive.com/snmpsoft-tools/snmp-get/) & [SnmpWalk](https://ezfive.com/snmpsoft-tools/snmp-walk/).

