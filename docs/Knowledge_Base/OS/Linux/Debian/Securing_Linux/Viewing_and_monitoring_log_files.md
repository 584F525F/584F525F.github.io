!!! info ""

    #### System logs
    
    System logs deal with exactly that - the Ubuntu system - as opposed to extra applications added by the user. These logs may contain information about authorizations, system daemons and system messages.
    
    ##### **Authorization log**
    
    Keeps track of authorization systems, such as password prompts, the sudo command and remote logins.
    
    ```bash
    /var/log/auth.log
    ```
    
    ##### **Daemon Log**
    
    Daemons are programs that run in the background, usually without user interaction. For example, display server, SSH sessions, printing services, bluetooth, and more.
    
    ```bash
    /var/log/daemon.log
    ```
    
    ##### **Debug log**
    
    Provides debugging information from the Ubuntu system and applications.
    
    ```bash
    /var/log/debug
    ```
    
    ##### **Kernel log**
    
    Logs from the Linux kernel.

    ```bash
    /var/log/kern.log
    ```

    
    ##### **System log**
    
    Contains more information about your system. If you can’t find anything in the other logs, it’s probably here.
    
    ```bash
    /var/log/syslog
    ```
    
    #### Application logs
    
    Some applications also create logs in 
    
    ```bash
    /var/log/
    ```

    **Below are some examples**
    
    ##### **Apache logs**

    Apache creates several log files in the /var/log/apache2/ subdirectory. The access.log file records all requests made to the server to access files. error.log records all errors thrown by the server.

    ```bash
    /var/log/apache2/
    ```
    
    ##### **X11 server logs**
  
    The X11 server creates a seperate log file for each of your displays. Display numbers start at zero, so your first display (display 0) will log to Xorg.0.log. The next display (display 1) would log to Xorg.1.log, and so on.

    ```bash
    /var/log/Xorg.0.log
    ```
        
    #### Non-human-readable logs
    
    Not all log files are designed to be read by humans. Some were made to be parsed by applications. Below are some of examples.
    
    ##### **Login failures log**
    
    Contains info about login failures. You can view it with the faillog command.
    
    ```bash
    /var/log/faillog
    ```
    
    ##### **Last logins log**
    
    Contains info about last logins. You can view it with the lastlog command.

    ```bash
    /var/log/lastlog
    ```
    
    ##### **Login records log**

    Contains login info used by other utilities to find out who’s logged in. To view currently logged in users, use the who command.

    ```bash
    /var/log/wtmp
    ```

!!! info ""
    
    ### Viewing logs using GNOME System Log Viewer
    
    The log viewer has a simple interface. The sidebar on the left shows a list of open log files, with the contents of the currently selected file displayed on the right.
    
    The log viewer not only displays but also monitors log files for changes. The bold text (as seen in the screenshot above) indicates new lines that have been logged after opening the file. When a log that is not currently selected is updated, it’s name in the file list will turn bold (as shown by auth.log in the screenshot above).
    
    Clicking on the cog at the top right of the window will open a menu allowing you to change some display settings, as well as open and close log files.
    
    There is also a magnifying glass icon to the right of the cog that allows you to search within the currently selected log file.
    
    GNOME System Log Viewer [official documentation](https://help.gnome.org/users/gnome-system-log/).
    

!!! info ""

    ### Viewing and monitoring logs from the command line
    
    #### Viewing files
    
     less file.txt
    
    #### Viewing the start or end of a file
    
    head and tail commands
    
    ```bash
    tail -n 15 file.txt
    head -n 15 [file.txt](https://file.txt)
    ```
    
    #### Monitoring files
    
    Pass the -f flag to tail. It will keep running, printing new additions to the file, until you stop it (Ctrl + C). For example:
    
    ```bash
    tail -f file.txt.
    ```
    
    #### Searching files
    
    ##### less
    ```bash
    less and press /. A
    ```

    ##### grep command
    To search for lines containing “test” in file.txt, you would run 
    
    ```bash
    grep "test" file.txt.
    ```
    
    If the result of a grep search is too long, you may pipe it to less, allowing you to scroll and search through it
    
    ```bash
    grep "test" file.txt | less.
    ```

!!! info ""
    Resources:
    [Log files locations](https://ubuntu.com/tutorials/viewing-and-monitoring-log-files#2-log-files-locations)
