```shell
# Sort a wordlist for the wordlist mode
tr A-Z a-z < SOURCE | sort -u > TARGET

# Use a potfile to generate a new wordlist
cut -d ':' -f 2 john.pot | sort -u pot.dic

# Generate candidate password for slow hashes
./john --wordlist=password.lst --stdout --rules:Jumbo | ./unique -mem=25 wordlist.uniq
--incremental:Lower # 26 char
--incremental:Alpha # 52 char
--incremental:Digits # 10 char
--incremental:Alnum # 62 char

# Create a new charset
./john --make-charset=charset.chr

# Then set the following in the John.conf
# Incremental modes
[Incremental:charset]
File = $JOHN/charset.chr
MinLen = 0
MaxLen = 31
CharCount = 95

# Using a specific charset
./john --incremental:charset hashFile
```