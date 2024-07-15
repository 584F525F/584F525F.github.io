!!! info ""

    ### Installing dnsutils

    ```bash
    sudo apt-get install dnsutils
    ```

    ### dnsutils Tools

    When installing dnsutils, you will be able to use the following commands
    
    - 'dig'
    - 'nslookup'
    - 'nsupdate'

    ### Command syntax

    #### dig

    ```bash
    dig [server] [name] [type]
    dig [@server] [-b address] [-c class] [-f filename] [-k filename] [-m] [-p port#] [-t type] [-x addr] [-y name:key] [-4] [-6] [name] [type] [class] [queryopt...]

    dig example.com
    dig example.com MX
    dig example.com SOA
    dig example.com TTL
    dig example.com ANY +noall +answer

    #reverse lookup
    dig -x 1.1.1.1 +short

    ```

    #### nslookup

    ```bash
    nslookup [-option] [name | -] [server]
    
    nslookup example.com
    nslookup -query=mx example.com
    nslookup -type=soa example.com
    nslookup -type=any example.com
    nslookup -timeout=10 example.com
    nslookup -port 56 example.com
    nslookup -debug example.com
    ```

    #### nsupdate

    ```bash
    nsupdate [-d] [[-y keyname:secret] | [-k keyfile]] [-t timeout] [-u udptimeout] [-r udpretries] [-v] [filename]
    ```
