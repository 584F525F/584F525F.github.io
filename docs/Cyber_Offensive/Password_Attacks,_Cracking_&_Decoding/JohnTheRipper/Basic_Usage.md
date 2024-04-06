
[Offensive Security Cheatsheet](https://cheatsheet.haax.fr/passcracking-hashfiles/john_cheatsheet/)

```shell
john hashfile.txt
john --wordlist=/path/to/your/wordlist.txt hashfile.txt
john --format=ntlm hashfile.txt
john --format=bcrypt hashfile.txt
```

##### ssh2john decrypt SSH private key
```shell
ssh2john id_rsa > crack.txt
john --wordlist=/usr/share/wordlists/rockyou.txt crack.txt
openssl rsa -in id_rsa
#Enter pass phrase for id_rsa: PASSWORD_HERE
```

##### gpg2john - Decrypted PGP file
```shell
gpg --import name.asc 
gpg2john name.asc > hash
john --format=gpg --wordlist=/usr/share/wordlists/rockyou.txt hash 
gpg --decrypt somecredentials.pgp # Enter the password found above. 
```

##### zip2john - Decrypt ZIP files
```shell
zip2john somezipname.zip > zipname.hash
john zipname.hash
7z e somezipname.zip
# Enter password (will not be echoed): PASSWORD_HERE
```

##### keepass2john
```shell
keepass2john some_pass_key.kdbx
```

##### rar2john
```shell
rar2john SOME_FILE.rar > crack_this
john --wordlist=/usr/share/wordlists/rockyou.txt crack_this
```

##### Wordlist Mode | Dictionnary attack
```shell
./john --wordlist=password.lst hashfile
```

##### Dictionnary attack using default or specific rules
```shell
./john --wordlist=password.lst --rules=rulename hashFile
./john --wordlist=password.lst --rules mypasswd
```

##### Mangling Rules Mode (hybrid)
```shell
./john --wordlist=password.lst – rules: hashfile
```

##### Incremental mode (Brute Force)
```shell
./john --incremental hashFile
./john --incremental hashfile External mode (use a program to generate guesses) ./john --external: hashfile
```

##### Loopback mode (use POT as wordlist)
```shell
./john --loopback hashFile
./john --loopback hashfile Mask mode (read MASK under /doc) ./john --mask=?1?1?1?1?1?1?1?1 -1=[A-Z] hashfile -min-len=8 
```

##### Hybrid Mask mode
```shell
./john -w=password.lst - mask='?l?l?w?l?l' hashfile
```

##### Mask bruteforce attack
```shell
./john --mask=?1?1?1?1?1?1 --1=[A-Z] hashFile --min-len=8
```

##### Dictionnary attack using masks
```shell
./john --wordlist=password.lst -mask='?l?l?w?l' hashFile
```

##### Markov mode (Read MARKOV under /doc).
```shell
---First-generate-Markov-stats:
./calc_stat wordlist markovstats
---Then-run:
./john -markov:200 -max-len:12 hashfile --mkv-stats=markovstats
```

##### Prince mode (Read PRINCE under /doc)
```shell
./john --prince=wordlist hashfile
```

##### Most modes have Maxlen=13 in John.conf but it can be overwritten with
```shell
-max-len=N up to 24
```
