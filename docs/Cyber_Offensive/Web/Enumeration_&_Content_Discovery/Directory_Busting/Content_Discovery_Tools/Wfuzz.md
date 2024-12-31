!!! info ""

    [wfuzz github](https://github.com/xmendez/wfuzz)

    ### Installation
    To install WFuzz, simply use pip:

    ```bash
    pip install wfuzz
    ```

    ### To run Wfuzz from a docker image, run:

    ```bash
    $ docker run -v $(pwd)/wordlist:/wordlist/ -it ghcr.io/xmendez/wfuzz wfuzz
    ```

    ### Documentation
    
    Documentation is available at http://wfuzz.readthedocs.io

    ### Download
    
    Check github releases. Latest is available at https://github.com/xmendez/wfuzz/releases/latest


!!! info ""

    ```bash
    
    #looking for common directories
    wfuzz -w wordlist/general/common.txt http://testphp.vulnweb.com/FUZZ

    #looking for common files:
    wfuzz -w wordlist/general/common.txt http://testphp.vulnweb.com/FUZZ.php

    #Fuzzing Parameters In URLs
    wfuzz -z range,0-10 --hl 97 http://testphp.vulnweb.com/listproducts.php?cat=FUZZ

    #Fuzzing POST Requests
    wfuzz -z file,wordlist/others/common_pass.txt -d "uname=FUZZ&pass=FUZZ"  --hc 302 http://testphp.vulnweb.com/userinfo.php

    #Fuzzing Cookies
    wfuzz -z file,wordlist/general/common.txt -b cookie=value1 -b cookie2=value2 http://testphp.vulnweb.com/FUZZ

    wfuzz -z file,wordlist/general/common.txt -b cookie=FUZZ http://testphp.vulnweb.com/

    #Fuzzing Custom headers
    wfuzz -z file,wordlist/general/common.txt -H "myheader: headervalue" -H "myheader2: headervalue2" http://testphp.vulnweb.com/FUZZ

    #You can modify existing headers, for specifying a custom user agent
    wfuzz -z file,wordlist/general/common.txt -H "myheader: headervalue" -H "User-Agent: Googlebot-News" http://testphp.vulnweb.com/FUZZ
    
    #Fuzzing HTTP Verbs
    wfuzz -z list,GET-HEAD-POST-TRACE-OPTIONS -X FUZZ http://testphp.vulnweb.com/

    #Authentication
    wfuzz -z list,nonvalid-httpwatch --basic FUZZ:FUZZ https://www.httpwatch.com/httpgallery/authentication/authenticatedimage/default.aspx

    #Recursion
    wfuzz -z list,"admin-CVS-cgi\-bin"  -R1 http://testphp.vulnweb.com/FUZZ
    ```

!!! info ""

    ### resources

    - https://www.hackingarticles.in/a-detailed-guide-on-wfuzz/
    - https://repo.zenk-security.com/Techniques%20d.attaques%20%20.%20%20Failles/WFUZZ%20for%20Penetration%20Testers.pdf
