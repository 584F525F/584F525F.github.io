```
tags:
    - windows
    - cmd
    - command prompt

```


!!! info ""

    The equivalent to the Linux command `;` as in

    ```shell
    echo "command 1" ; echo "command 2"
    ```

    is

    ```shell
    dir & whoami
    ```

!!! info ""

    ### File operations

    Delete file

    ```shell
    del
    ```

    Create folder/directory

    ```shell
    md folderName
    ```

    Show hidden files

    ```shell
    dir /A
    ```

    Print out file content, like cat

    ```shell
    type file.txt
    ```

    grep files

    ```shell
    findstr file.txt
    ```

!!! info ""

    ### Network

    Show network information

    ```shell
    netstat -an
    ```

    Show network adapter info

    ```shell
    ipconfig
    ```

    Ping another machine

    ```shell
    ping 192.168.1.101
    ```

    Traceroute

    ```shell
    tracert
    ```

!!! info ""

    ### Processes

    List processes

    ```shell
    tasklist
    ```

    Kill a process

    ```shell
    taskkill /PID 1532 /F
    ```

!!! info ""

    ### Users

    ```shell
    net users

    # Add user
    net user hacker my_password /add
    net localgroup Administrator hacker /add

    # Check if you are part of a domain
    net localgroup /domain

    # List all users in a domain
    net users /domain
    ```

!!! info ""

    ### Mounting - Mapping

    In the windows world mounting is called mapping.

    If you want to see which drives are mapped/mounted to your file-system you can use any of these commands:

    ```shell
    # This is the most thorough
    wmic logicaldisk get deviceid, volumename, description

    # But this works too
    wmic logicaldisk get name
    wmic logicaldisk get caption

    # This can be slow. So don't kill your shell!
    fsutil fsinfo drives

    # With powershell
    get-psdrive -psprovider filesystem

    # This works too, but it is interacive. So it might be dangerous work hackers
    diskpart
    list volume

    # Map only network drives
    net use
    ```

    The command to deal with mounting/mapping is net use

    Using `net use` we can connect to other shared folder, on other systems. Many windows machines have a default-share called IPC (Interprocess communication share). It does not contain any files. But we can usually connect to it without authentication. This is called a null-session. Although the share does not contain any files it contains a lot of data that is useful for enumeration. The Linux-equivalent of `net use` is usually `smbclient`.

    ```shell
    net use \\IP address\IPC$ "" /u:""
    net use \\192.168.1.101\IPC$ "" /u:""
    ```

    If you want to map a drive from another network to your filesystem you can do that like this:

    ```shell
    # This will map it to drive z
    net use z: \\192.168.1.101\SYSVOL

    # This will map it to the first available drive-letter
    net use * \\192.168.1.101\SYSVOL
    ```

    Here you map the drive to the letter `z`. If the command is successful you should now be able to access those files by entering the `z` drive.

    You enter the z-drive by doing this:

    ```shell
    C:\>z:
    Z:\

    # Now we switch back to c
    Z:\>c:
    C:\
    ```

    Remove a network drive - umount it

    First leave the drive if you are in it:

    ```shell
    c:
    net use z: /del
    ```


!!! info ""

    ### Other

    Shutdown

    ```shell
    # Shutdown now
    shutdown /s /t 0

    # Restart
    shutdown /r /t 0
    ```

    ciper - Clear data/shred

    ```shell
    Shreds the whole machine
    ciper /w:C:\
    ```

    Show environmental variables

    ```shell
    set
    ```

    Show options for commands

    The "man"-pages in windows is simply:

    ```shell
    help dir
    ```


!!! info ""

    ### References

    This might come in handy for the linux-users [lemoda windows2unix](http://www.lemoda.net/windows/windows2unix/windows2unix.html)
