
!!! info ""

    ### apidork

    [apidork](https://github.com/sameerfakhoury/apidork)

    ```bash
    git clone https://github.com/sameerfakhoury/apidork.git
    cd apidork
    pip install -r requirements.txt
    python3 apidork.py
    ```

    now you are ready to use the tool and check each option with the corresponding information to use with

    usage

    Syntax: python3 apidork.py -option1 "value1" -option2 "value2" Options to use:

    ```bash
    1. username search: -u "user_name" -- example: python3 apidork.py -u "example"                                                              
    2. files related to domain: -d "domain_name" -f "file_extension" -- example: python3 apidork.py -d "example.com" -f "pdf"                   
    3. text in website: -url "full_url" -t "keyword" -- example: python3 apidork.py -url "https://example.com/index.html" -t "helloword"        
    4. restrict search to domain : -d "domain_name" -- example: python3 apidork.py -d "xxx.xxx.xx"                                              
    5. links title with keyword: -k "title_keyword" -- example: python3 apidork.py -k "xxxxxxxxxx"                                            
    6. extract location information: -lat "latitude" -lon "longitude" -- example: python3 apidork.py -lat "xx.xxx..." -lon "xx.xxx..."          
    7. extract location coordinates: -l "location_name" -- example: python3 apidork.py -l "xxxx xxx xx ..."                                     
    8. extract IP informations: -ip "ip" -- example: python3 apidork.py -ip "x.x.x.x"                                                           
    9. check your public IP: -myip -- example: python3 apidork.py -myip
    10. extract Zip/postal code informations: -c "country" -z "zipcode" -- example: python3 -c "xx" -z "xxxxx"                                  
    ```


!!! info ""

    ### Dorks eye

    [dorks eye - hackingpassion](https://hackingpassion.com/dorks-eye-google-hacking-dork-scraping-and-searching-script/)
    [dorks eye - github](https://github.com/Bullseye0/google_dork_list?tab=readme-ov-file)


!!! info ""

    [pagodo github](https://github.com/opsdisk/pagodo)

    

!!! info ""

    ### DorkFinder

    [DorkFinder- github](https://github.com/glavstroy/DorkFinder?tab=readme-ov-file)

    #### Install on Linux
    
    ```bash
    git clone https://github.com/glavstroy/DorkFinder
    cd DorkFinder
    pip install -r requirements
    ```

    #### Install on Docker

    ```bash
    git clone https://github.com/glavstroy/DorkFinder
    cd DorkFinder
    sudo docker build . -t dorkfinder
    sudo docker run -it --rm dorkfinder
    ```

    #### Switches/Flags

    |Flag | Description|
    |:-|:-|
    |-h/--help	|show this help message and exit|
    |-t	|enter the target domain|
    |-o	|print to output.txt|

    #### Usage

    ```bash
    python3 dorkfinder.py -t example.com -o
    ```



