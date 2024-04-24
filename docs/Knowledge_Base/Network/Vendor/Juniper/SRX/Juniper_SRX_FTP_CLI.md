
#### Enabling ftp on Juniper

```bash
configure
set system services ftp
set security zones security-zone MGMT interfaces irb.100 ost-inbound-traffic system-services ftp					set security ones security-zone MGMT interfaces ge-0/0/4.100 host-inbound-traffic ystem-services ftp
commit confirmed
```

This gives FTP on LAN side so use VPN IP to connect

Uploading the files
- You can use an FTP Client such as WinSCP or FileZilla to upload the files, you can check the article explaining how to use FTPZilla [FileZilla FTP Client]
- Make sure you have the following path & directories created /cf/var/home/ftpuser If the ftpuser directory is missing then create it.
- Upload all the files to /cf/var/home/ftpuser/
- The ftp link that you should be using to login and get the files should be something like this ftp://ftpuser:ftpuser123@<IP Address>/FileName YOU MUST USE THE LOCAL PRIVATE IP ADDRESS FOR THE FTP SERVER
- Example link: ftp://ftpuser:ftpuser123@10.10.10.1/firmwarefile.bin
  - This link will directly go into the Directory /cf/var/home/ftpuser/ and get the files named  and listed there. cf/var/home/ftpuser

#### Disabling FTP

```bash
configure
delete system login user ftpuser
delete system services ftp
delete security zones security-zone MGMT interfaces irb.100 ost-inbound-traffic system-services ftp
commit confirmed
Commit
```

#### Delete files

```bash
Exit
Start shell
ls
Rm (file_name)
exit
```
