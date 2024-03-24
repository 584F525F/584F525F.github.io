## John - Basic Usage

##### Basic usage

```shell
john hashfile.txt
john --wordlist=/path/to/your/wordlist.txt hashfile.txt
john --format=ntlm hashfile.txt
john --format=bcrypt hashfile.txt
```

##### ssh2john - Decrypt SSH Private Keys - id_rsa

```shell
ssh2john id_rsa > crack.txt
john --wordlist=/usr/share/wordlists/rockyou.txt crack.txt
openssl rsa -in id_rsa
# Enter pass phrase for id_rsa: PASSWORD_HERE
```

##### gpg2john - Decrypt PGP file .asc

```bash
gpg --import name.asc 
gpg2john name.asc > hash
john --format=gpg --wordlist=/usr/share/wordlists/rockyou.txt hash 
gpg --decrypt somecredentials.pgp  # Enter the password found above. 
```

##### keepass2john

```bash
keepass2john some_pass_key.kdbx
```

##### zip2john - crack zip files

```bash
zip2john somezipname.zip > zipname.hash
john zipname.hash 
7z e somezipname.zip
# Enter password (will not be echoed): PASSWORD_HERE
```

##### rar2john

```bash
rar2john SOME_FILE.rar > crack_this
john --wordlist=/usr/share/wordlists/rockyou.txt crack_this
```
