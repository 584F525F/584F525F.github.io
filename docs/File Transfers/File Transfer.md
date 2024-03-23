### Telnet

```bash
telnet ip_address
ls
PASV
TYPE A
STAT
get Download.txt
put Upload.txt
Exit
```

### FTP - File Transfer Protocol

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

### SCP - Secure Copy Protocol

#### commands

```shell
scp <options> <source_path> <destination_path>
scp o s_path d_path

#specifying port with -P
scp -P 5562 file <username>@<remotehost_ip>:</path/to/file>
scp -P 5562 f? u@ip:r_file_path

# uploading a file
scp file <username>@<remotehost_ip>:</path/to/file>
scp file u@ip:r_file_path

# uploading multiple files
scp file1 file2 <username>@<remotehost_ip>:</path/to/directory>
scp f? f? u@ip:r_dir_path

# downloading a file
scp <username>@<remotehost_ip>:</path/to/file> </local/path/to/file>
scp u@ip:r_file_path l_file_path

# downloading multiple files
scp <username>@<remotehost_ip>:</path/directory/\{file.txt,file2.txt\}> .
scp u@ip:dir_path/\f?,f? .

# downloading a directory 
scp -r </path/to/directory> <username>@<ip_address>:</path/to/directory>
scp -r l_dir_path u@ip:r_dir_path
```

#### switches

```shell
-r      # transfer directory 
-v      # see the transfer details
-C      # copy files with compression
-l 800  # limit bandwidth with 800
-p      # preserving the original attributes of the copied files
-P      # connection port
-q      # hidden the output
```

### ftpd

```shell
/etc/init.d/pure-ftpd
```

