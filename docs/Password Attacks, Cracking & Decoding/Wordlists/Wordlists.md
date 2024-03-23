
> [!NOTE] Resources
> https://github.com/kaonashi-passwords/Kaonashi
> https://github.com/tarraschk/richelieu
>https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt
>https://packetstormsecurity.com/Crackers/wordlists/page4/
>http://www.gwicks.net/dictionaries.htm
>>##### SCADA Default Passwords
>http://www.critifence.com/default-password-database/
>https://weakpass.com/
>https://github.com/berzerk0/Probable-Wordlists
>>##### Looks very cool wordlists
>https://github.com/FlameOfIgnis/Pwdb-Public


```shell title:"Wordlists"
sudo apt-get install seclists
ls /usr/share/wordlists
----------------------------------------------------------------------------------
#CeWL 
# CeWL allows you to build custom wordlists based on online resources
# If you know that your target is target.com, you can parse web content to build lists
# Can be time consuming

# 5 levels of depth and minimum 7 char per word
cewl -w customwordlist.txt -d 5 -m 7 www.sans.org

# Also visit and parse other sites
cewl -w customwordlist.txt -d 5 -m 7 -o www.sans.org

# Include e-mail adresses
cewl -w customwordlist.txt -d 5 -m 7 -e www.sans.org

----------------------------------------------------------------------------------
PACK 
# Password Analysis and Cracking Kit 
# You can get stats about already cracked passwords
# In order to define new masks
https://github.com/iphelix/pack

python statsgen.py rockyou.txt

----------------------------------------------------------------------------------
Combinator 
# Combinator is part of the hashcat-utils
# It can be used to prepare a combinated wordlist for cracking
# It allows then to combination + others settings like masks or rules
combinator.exe file1 file2

# It can create MASSIVE wordlists and take some time to run.

# Three files combination
combinator2.exe file1 file2 file3

# You can also feed output directly to hashcat
combinator.exe file1 file2 | hashcat -m x hashs.file -a 0 --force -O

```

