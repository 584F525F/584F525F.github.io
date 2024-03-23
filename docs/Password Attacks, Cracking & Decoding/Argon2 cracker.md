[Argon2 Cracker Github](https://github.com/CyberKnight00/Argon2_Cracker)

#### install
```shell
git clone https://github.com/CyberKnight00/Argon2_Cracker.git
pip3 install -r requirement.txt
chmod +x crack_argon2.py
```

####  To specify custom wordlist -w opting is to be supply.
```shell
./crack_argon2.py -c '< Argon2 Hash >' -w '< Path/To/Wordlist >'
```

####  In this command -c option is used to specify Argon2id type hash & -v for Verbose output.
```shell
# Default wordlist is used
./crack_argon2.py -c '< Argon2 Hash >' -v
```

#### In this command -c option is used to specify Argon2id type hash.
```shell
# Default word-list (/usr/share/wordlists/fasttrack.txt) is used if no wordlist is specified.
./crack_argon2.py -c '< Argon2 hash >'
```