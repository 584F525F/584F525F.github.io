
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
