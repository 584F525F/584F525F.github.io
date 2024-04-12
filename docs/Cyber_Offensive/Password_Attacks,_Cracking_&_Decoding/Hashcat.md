!!! info ""
    ### Sources
    - [hashcat\_user\_manual](https://doc.callmematthi.eu/static/webArticles/hashcat_user_manual.pdf)
    - [hashcat hash list](https://hashcat.net/wiki/doku.php?id=example_hashes)
    - [Offensive Security Cheatsheet](https://cheatsheet.haax.fr/passcracking-hashfiles/hashcat_cheatsheet/)
    
!!! info ""

    ### switches

    ```shell
    #attack modes
    -a 0 # Straight : hash dict
    -a 1 # Combination : hash dict dict
    -a 3 # Bruteforce : hash mask
    -a 6 # Hybrid wordlist + mask : hash dict mask
    -a 7 # Hybrid mask + wordlist : hash mask dict
    ------------------------------------------------------------------------
    #Charsets 
    ?l # Lowercase a-z
    ?u # Uppercase A-Z
    ?d # Decimals
    ?h # Hex using lowercase chars
    ?H # Hex using uppercase chars
    ?s # Special chars
    ?a # All (l,u,d,s)
    ?b # Binary
    ------------------------------------------------------------------------
    #options
    -m # Hash type
    -a # Attack mode
    -r # Rules file
    -V # Version
    --status # Keep screen updated
    -b # Benchmark
    --runtime # Abort after X seconds
    --session [text] # Set session name
    --restore # Restore/Resume session
    -o filename # Output to filename
    --username # Ignore username field in a hash
    --potfile-disable # Ignore potfile and do not write
    --potfile-path # Set a potfile path
    -d # Specify an OpenCL Device
    -D # Specify an OpenCL Device Type
    -l # List OpenCL Devices & Types
    -O # Optimized Kernel, Passwords <32 chars
    -i # Increment (bruteforce)
    --increment-min # Start increment at X chars
    --increment-max # Stop increment at X charset 
    ```

!!! info ""

    ### commands

    #### Hashcat SHA512 $6$ shadow file

    ```bash
    hashcat -m 1800 -a 0 hash.txt rockyou.txt --username
    ```

    #### Hashcat MD5 $1$ shadow file

    ```bash
    hashcat -m 500 -a 0 hash.txt rockyou.txt --username
    ```

    #### Hashcat MD5 Apache webdav file

    ```bash
    hashcat -m 1600 -a 0 hash.txt rockyou.txt
    ```

    #### Hashcat SHA1

    ```bash
    hashcat -m 100 -a 0 hash.txt rockyou.txt --force
    ```

    #### Hashcat Wordpress

    ```bash
    hashcat -m 400 -a 0 --remove hash.txt rockyou.txt
    ```

    #### Benchmark MD4 hashes

    ```bash
    hashcat -b -m 900
    ```

    #### Create a hashcat session to hash Kerberos 5 tickets using wordlist

    ```bash
    hashcat -m 13100 -a 0 --session crackin1 hashes.txt wordlist.txt -o output.pot
    ```

    #### Crack MD5 hashes using all char in 7 char passwords

    ```bash
    hashcat -m 0 -a 3 -i hashes.txt ?a?a?a?a?a?a?a -o output.pot
    ```

    #### Crack SHA1 by using wordlist with 2 char at the end 

    ```bash
    hashcat -m 100 -a 6 hashes.txt wordlist.txt ?a?a -o output.pot
    ```

    #### Crack WinZip hash using mask (Summer2018!)

    ```bash
    hashcat -m 13600 -a 3 hashes.txt ?u?l?l?l?l?l?l?d?d?d?d! -o output.pot
    ```

    #### Crack MD5 hashes using dictionnary and rules

    ```bash
    hashcat -a 0 -m 0 example0.hash example.dict -r rules/best64.rules
    ```

    #### Crack MD5 using combinator function with 2 dictionnaries

    ```bash
    hashcat -a 1 -m 0 example0.hash example.dict example.dict
    ```

    #### Cracking NTLM hashes

    ```bash
    hashcat64 -m 1000 -a 0 -w 4 --force --opencl-device-types 1,2 -O d:\hashsample.hash "d:\WORDLISTS\realuniq.lst" -r OneRuleToRuleThemAll.rule
    ```

    #### Cracking hashes from kerberoasting

    ```bash 
    hashcat64 -m 13100 -a 0 -w 4 --force --opencl-device-types 1,2 -O d:\krb5tgs.hash d:\WORDLISTS\realhuman_phill.txt -r OneRuleToRuleThemAll.rule
    ```

    #### You can use hashcat to perform combined attacks

    ```bash 
    # For example by using wordlist + mask + rules
    hashcat -a 6 -m 0 prenoms.txt ?d?d?d?d -r rules/yourule.rule
    ```

    #### Single rule used to uppercase first letter --> Marie2018

    ```bash 
    hashcat -a 6 -m 0 prenoms.txt ?d?d?d?d -j 'c'
    ```
