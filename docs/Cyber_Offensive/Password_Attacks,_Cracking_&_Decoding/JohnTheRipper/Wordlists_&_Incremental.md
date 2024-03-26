##### Sort a wordlist for the wordlist mode
```shell
tr A-Z a-z < SOURCE | sort -u > TARGET
```

##### Use a potfile to generate a new wordlist
```shell
cut -d ':' -f 2 john.pot | sort -u pot.dic
```

##### Generate candidate password for slow hashes
```shell
./john --wordlist=password.lst --stdout --rules:Jumbo | ./unique -mem=25 wordlist.uniq
--incremental:Lower # 26 char
--incremental:Alpha # 52 char
--incremental:Digits # 10 char
--incremental:Alnum # 62 char
```

##### Create a new charset
```shell
./john --make-charset=charset.chr
```

##### Then set the following in the John.conf
Incremental modes
```shell
[Incremental:charset]
File = $JOHN/charset.chr
MinLen = 0
MaxLen = 31
CharCount = 95
```

##### Using a specific charset
```shell
./john --incremental:charset hashFile
```
