!!! info "FTP - File Transfer Protocol"

    #### commands

    ```bash
    ftp ip_address
    #enter username
    #enter password

    #print working directory
    pwd

    #list file in directory
    ls

    #change working directory
    cd /dir/dir
    cd ../dir
    cd ..
    cdup

    #creating directory
    mkdir new_dir

    #removing directory
    rmdir new_dir

    #change transfer mode
    ascii #suitable for transferring text data such as HTML files.
    binary #

    #download and upload a file
    get Download.txt
    put Upload.txt

    #download upload multiple files
    mget *.txt
    mget file?.txt file?.zip
    mput file.jpg file.jpg
    mput *.zip

    #delete file | multiple files
    delete file.zip
    mdelete *.zip

    #rename a file
    rename name.txt new_name.txt

    # append remote file data
    append new_data.sh old_data.sh

    #change file permissions
    chmod 777 file.sh
    chmod +x file.sh

    #to exit
    bye
    exit
    quit
    ```

!!! info "FTP options"

    #### switches

    ```bash
    -4	Use only IPv4 to contact any host.
    -6	Use IPv6 only.
    -e	Disables command editing and history support, if it was compiled into the ftp executable. Otherwise, it does nothing.
    -p	Use passive mode for data transfers. Allows the use of ftp in environments where a firewall prevents connections from the outside world back to the client machine. Requires the ftp server to support the PASV command .
    -i	Turns off interactive prompting during multiple file transfers.
    -n	Restrains ftp from attempting auto-login upon initial connection. If auto-login is enabled, ftp checks the .netrc (see netrc ) file in the user’s home directory for an entry describing an account on the remote machine. If no entry exists, ftp prompts for the remote machine login name (the default is the user identity on the local machine), and, if necessary, prompt for a password and an account with which to login.
    -g	Disables file name globbing.
    -v	The verbose option forces ftp to show all responses from the remote server, as well as report on data transfer statistics.
    -d	Enables debugging.
    ```
