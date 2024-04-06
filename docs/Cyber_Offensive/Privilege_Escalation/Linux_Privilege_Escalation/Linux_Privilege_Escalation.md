??? example "common checks"
    ### common checks
    #### Kernal check

    ```bash
    #Kernal version
    uname -a
    cat /proc/version
    cat /etc/issue
    ```

    #### CPU

    ```shell
    #Checking CPU Cores vs the resources an exploit might need to avoid running an exploit that exceeds CPU on system
    #Check ARCHETICTURE
    lscpu
    ```

    #### Running Services

    ```shell
    #show running services - they are in order of execution, top is oldest and bottom is latest
    ps aux

    #pull all services running by root
    #you canchange root to any username
    ps aux | grep root
    ```

    #### writable Paths | SUID | CAP

    ```shell
    #find writable paths
    find / -writable 2>/dev/null | grep home

    #SUID bit - denoted as s. 
    find / -type f -perm -04000 -ls 2>/dev/null | awk '{print $3, $5, $6, $NF}' | grep /usr/bin/. 
    find / -type f -perm -04000 -ls 2>/dev/null

    #get capabilities
    getcap -r / 2>/dev/null

    [GTFOBins](https://gtfobins.github.io/)

    ```

    #### Privileges

    ```shell
    #see the user privileges
    id

    #what services can you run as root without needing a root password
    sudo -l

    #users
    cat /etc/passwd
    cat /etc/passwd | cut -d :  -f 1         #d for delimeter   #f for field   

    #passwords
    cat /etc/shadow

    #The group file
    cat /etc/group

    #escalate to another user or root user
    sudo su -
    ```

    #### misc

    ```shell
    #in a command line the single quotes take precedence
    ping 8.8.8.8 | 'ls'   >  will print ls

    #checking $PATH env variable
    print $PATH

    #check command history
    cat ~/.bash_history | grep -i passw

    #check bash history
    ls -la
    cat .bash_history 

    ```

    #### looking up password

    ```shell
    #grep anything that contains the word password and color it red
    grep --color=auto -rnw '/' -ie "PASSWORD=" --color=always 2> /dev/null
    #find pasword named files
    locate password | more
    locate pass | more
    locate pwd | more
    find / -name authorized_keys 2> /dev/null
    find / -name id_rsa 2> /dev/null
    ```


??? example "Crontab Cronjobs | process explore"
    ### Crontab Cronjobs | process explore
    #### strace 

    ```shell
    strace /usr/local/bin/suid-env
    ```

    #### strings - see what the comand is doing

    ```shell
    strings /usr/local/bin/suid-env
    ```

??? example "automated tools 👾"
    ### automated tools
    [LinEnum](https://github.com/rebootuser/LinEnum)

