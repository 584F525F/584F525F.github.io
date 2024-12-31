!!! info ""

    ##### Sort a wordlist for the wordlist mode

    ```bash
    tr A-Z a-z < SOURCE | sort -u > TARGET
    ```

    ##### Use a potfile to generate a new wordlist

    ```bash
    cut -d ':' -f 2 john.pot | sort -u pot.dic
    ```

    ##### Generate candidate password for slow hashes

    ```bash
    ./john --wordlist=password.lst --stdout --rules:Jumbo | ./unique -mem=25 wordlist.uniq
    --incremental:Lower # 26 char
    --incremental:Alpha # 52 char
    --incremental:Digits # 10 char
    --incremental:Alnum # 62 char
    ```

    ##### Create a new charset

    ```bash
    ./john --make-charset=charset.chr
    ```

    ##### Then set the following in the John.conf

    Incremental modes
    ```bash
    [Incremental:charset]
    File = $JOHN/charset.chr
    MinLen = 0
    MaxLen = 31
    CharCount = 95
    ```

    ##### Using a specific charset

    ```bash
    ./john --incremental:charset hashFile
    ```
