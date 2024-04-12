!!! info ""
    [dirb](https://salsa.debian.org/pkg-security-team/dirb)

    no wordlists needed to specify, tool chooses for you

    ```shell

    dirb http://192.168.1.106/dvwa/

    #search for extension file type
    dirb http://192.168.1.106/dvwa/ -X .php

    #output to file
    dirb http://192.168.1.106/dvwa/ -o output.txt

    #ignore return code 302
    dirb http://192.168.1.106/dvwa/ -N 302

    #do in  depth scan and don't avoid warning messages
    dirb http://192.168.1.106/ -w

    #speed delay in ms
    dirb http://192.168.1.106/dvwa -z  100

    #don't recusive scan
    dirb http://192.168.1.106/dvwa -r

    #find none existant pages such as error code pages
    dirb http://192.168.1.106/dvwa -v

    #extension list and header
    dirb http://192.168.1.106/dvwa -H .php

    #Http Autherization username:password
    dirb http://testphp.vulnweb.com/login.php -u  username:password

    #Proxy URL such as page Access Forbiden, it exists behind some proxy
    dirb http://192.168.1.108 –p 192.168.1.108:3129

    ```
