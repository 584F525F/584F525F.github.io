```shell title:"John Cracking Modes" fold:folded
#Wordlist Mode | Dictionnary attack
./john --wordlist=password.lst hashfile

#Dictionnary attack using default or specific rules
./john --wordlist=password.lst --rules=rulename hashFile
./john --wordlist=password.lst --rules mypasswd

#Mangling Rules Mode (hybrid)
./john --wordlist=password.lst – rules: hashfile

#Incremental mode (Brute Force)
./john --incremental hashFile
./john --incremental hashfile External mode (use a program to generate guesses) ./john --external: hashfile

#Loopback mode (use POT as wordlist)
./john --loopback hashFile
./john --loopback hashfile Mask mode (read MASK under /doc) ./john --mask=?1?1?1?1?1?1?1?1 -1=[A-Z] hashfile -min-len=8 

#Hybrid Mask mode
./john -w=password.lst - mask='?l?l?w?l?l' hashfile

# Mask bruteforce attack
./john --mask=?1?1?1?1?1?1 --1=[A-Z] hashFile --min-len=8

# Dictionnary attack using masks
./john --wordlist=password.lst -mask='?l?l?w?l' hashFile

#Markov mode (Read MARKOV under /doc).
---First-generate-Markov-stats:
./calc_stat wordlist markovstats
---Then-run:
./john -markov:200 -max-len:12 hashfile --mkv-stats=markovstats

#Prince mode (Read PRINCE under /doc)
./john --prince=wordlist hashfile

#Most modes have Maxlen=13 in John.conf but it can be overwritten with
-max-len=N up to 24



```