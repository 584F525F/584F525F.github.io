
```shell title:"John Basics" fold:folded
#Basic Usage
john hashfile.txt
john --wordlist=/path/to/your/wordlist.txt hashfile.txt
john --format=ntlm hashfile.txt
john --format=bcrypt hashfile.txt

#ssh2john
#Encrypted SSH private key found? Crack it with ssh2john
 1) ssh2john id_rsa > crack.txt
 2) john --wordlist=/usr/share/wordlists/rockyou.txt crack.txt
 3) openssl rsa -in id_rsa
    Enter pass phrase for id_rsa: PASSWORD_HERE
	
#gpg2john
#Encrypted PGP file found? Crack it with gpg2john
gpg --import name.asc 
gpg2john name.asc > hash
john --format=gpg --wordlist=/usr/share/wordlists/rockyou.txt hash 
gpg --decrypt somecredentials.pgp        # Enter the password found above. 

#zip2john
#Encrypted ZIP file found? Crack it with zip2john
1) zip2john somezipname.zip > zipname.hash
2) john zipname.hash 
3) 7z e somezipname.zip
   Enter password (will not be echoed): PASSWORD_HERE
   
#keepass2john
keepass2john some_pass_key.kdbx

#rar2john
rar2john SOME_FILE.rar > crack_this
john --wordlist=/usr/share/wordlists/rockyou.txt crack_this
```
