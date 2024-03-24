# nmap

```shell
sudo nmap -sV -A --min-rate 1500 x.x.x.x
sudo nmap -p x,x,x --script vuln x.x.x.x
```

# metasploit
```shell
systemctl start postgresql
msfdb init
msfconsole
db_status
workspace -a <project_name>
workspace

db_nmap -sV -A -p- x.x.x.x
hosts
services
vulns

```

# Nikto
[Nikto web server scanner](https://github.com/sullo/nikto)
