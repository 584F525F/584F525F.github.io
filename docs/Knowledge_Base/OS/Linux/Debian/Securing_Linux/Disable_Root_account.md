!!! warning ""

    #### 0. Create a user

    First steps to securing your linux machine after install
    Create a new user

    ```bash
    sudo adduser <user-name>
    #enter password and confirm
    #you can skip the info it asks you (full name, ...), just hit enter until it's done
    ```

    example

    ```bash
    [sudo] password for batman:
    Adding user `batmanss' ...
    Adding new group `batman' (1001) ...
    Adding new user `batman' (1001) with group `batman' ...
    Creating home directory `/home/batman' ...
    Copying files from `/etc/skel' ...
    New password:
    Retype new password:
    passwd: password updated successfully
    Changing the user information for batman
    Enter the new value, or press ENTER for the default
        Full Name []:
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
    Is the information correct? [Y/n]
    ```

    #### 1. Disable root login usermod	

    ```bash
    sudo usermod -L root
    ```

!!! warning ""
    
    #### 2. Change root User’s Shell
    This method is only effective with programs that require a shell for user login, otherwise, sudo, ftp and email clients can access the root account.

    ```bash
    sudo usermod -s /usr/sbin/nologin root
    cat /etc/passwd | grep root
    ```

    Change root login message from default message

    ```bash
    sudo nano /etc/nologin.txt
    ```
    
    Enter your prefered warning message, then save your changes and exit the file
    The the ducks are qucking around, so watch your back Jack!
    
    Cat the message

    ```bash
    cat /etc/nologin.txt
    ```

!!! warning ""
    
    #### 3. Disable SSH Root Login
    This method only affects openssh tools set, programs such as ssh, scp, sftp will be blocked from accessing the root account.

    ```bash
    sudo nano /etc/ssh/sshd_config
    #### uncomment below
    PermitRootLogin no
    ```

    restart ssh service

    ```bash
    sudo systemctl restart sshd 
    ```

!!! warning ""
    
    #### 4. Restrict root Acess to Services Via PAM [Pluggable Authentication Modules]
    This method only affect programs and services that are PAM aware. You can block root access to the system via ftp and email clients and more.

    ```bash
    cat /etc/passwd | grep 1000
    #### EDIT THE USERS ALLOWED userx
    echo -e "user1\nuser2\nuser3" | sudo tee /etc/allowed_users
    sudo nano /etc/pam.d/sshd
    #### Add at the beginning of the file
    auth required pam_listfile.so item=user sense=allow file=/etc/allowed_users onerr=fail
    ```

    restart ssh service

    ```bash
    sudo systemctl restart ssh
    ```
