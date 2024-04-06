SCP - Secure Copy Protocol

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

