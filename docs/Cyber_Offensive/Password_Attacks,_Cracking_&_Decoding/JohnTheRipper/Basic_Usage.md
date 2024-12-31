!!! info ""
    sources:
    [Offensive Security Cheatsheet](https://cheatsheet.haax.fr/passcracking-hashfiles/john_cheatsheet/)

!!! info ""

    ```bash
    john hashfile.txt
    john --wordlist=/path/to/your/wordlist.txt hashfile.txt
    john --format=ntlm hashfile.txt
    john --format=bcrypt hashfile.txt
    ```
    
    ##### ssh2john decrypt SSH private key

    ```bash
    ssh2john id_rsa > crack.txt
    john --wordlist=/usr/share/wordlists/rockyou.txt crack.txt
    openssl rsa -in id_rsa
    #Enter pass phrase for id_rsa: PASSWORD_HERE
    ```

    ##### gpg2john - Decrypted PGP file

    ```bash
    gpg --import name.asc 
    gpg2john name.asc > hash
    john --format=gpg --wordlist=/usr/share/wordlists/rockyou.txt hash 
    gpg --decrypt somecredentials.pgp # Enter the password found above. 
    ```

    ##### zip2john - Decrypt ZIP files

    ```bash
    zip2john somezipname.zip > zipname.hash
    john zipname.hash
    7z e somezipname.zip
    # Enter password (will not be echoed): PASSWORD_HERE
    ```

    ##### keepass2john

    ```bash
    keepass2john some_pass_key.kdbx
    ```

    ##### rar2john

    ```bash
    rar2john SOME_FILE.rar > crack_this
    john --wordlist=/usr/share/wordlists/rockyou.txt crack_this
    ```

    ##### Wordlist Mode | Dictionnary attack

    ```bash
    ./john --wordlist=password.lst hashfile
    ```

    ##### Dictionnary attack using default or specific rules

    ```bash
    ./john --wordlist=password.lst --rules=rulename hashFile
    ./john --wordlist=password.lst --rules mypasswd
    ```

    ##### Mangling Rules Mode (hybrid)

    ```bash
    ./john --wordlist=password.lst – rules: hashfile
    ```

    ##### Incremental mode (Brute Force)

    ```bash
    ./john --incremental hashFile
    ./john --incremental hashfile External mode (use a program to generate guesses) ./john --external: hashfile
    ```

    ##### Loopback mode (use POT as wordlist)

    ```bash
    ./john --loopback hashFile
    ./john --loopback hashfile Mask mode (read MASK under /doc) ./john --mask=?1?1?1?1?1?1?1?1 -1=[A-Z] hashfile -min-len=8 
    ```

    ##### Hybrid Mask mode

    ```bash
    ./john -w=password.lst - mask='?l?l?w?l?l' hashfile
    ```

    ##### Mask bruteforce attack

    ```bash
    ./john --mask=?1?1?1?1?1?1 --1=[A-Z] hashFile --min-len=8
    ```

    ##### Dictionnary attack using masks

    ```bash
    ./john --wordlist=password.lst -mask='?l?l?w?l' hashFile
    ```

    ##### Markov mode (Read MARKOV under /doc)

    ```bash
    ---First-generate-Markov-stats:
    ./calc_stat wordlist markovstats
    ---Then-run:
    ./john -markov:200 -max-len:12 hashfile --mkv-stats=markovstats
    ```

    ##### Prince mode (Read PRINCE under /doc)

    ```bash
    ./john --prince=wordlist hashfile
    ```

    ##### Most modes have Maxlen=13 in John.conf but it can be overwritten with

    ```bash
    -max-len=N up to 24
    ```
