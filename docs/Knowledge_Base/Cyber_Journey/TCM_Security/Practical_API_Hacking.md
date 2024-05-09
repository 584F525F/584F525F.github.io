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
    
        Good resource for THM Bookstore Room [Bookstore writeup](https://systemweakness.com/bookstore-writeup-tryhackme-api-hacking-reverse-engineering-c4b50ac93689)










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



	
!!! info ""

    ## The Labs

    !!! example ""

        ### BFLA Lab

        [BFLA Lab](https://academy.tcm-sec.com/courses/2008721/lectures/45992140)

        To get the vAPI application
        
        ```bash
        git clone https://github.com/roottusk/vapi
        #The collection is in the "postman" folder
        #If you don't have git, you can use:
        sudo apt install git
        ```

    !!! example ""

        ### BFLA Lab

        [BFLA Lab](https://academy.tcm-sec.com/courses/2008721/lectures/45992498)

        To get the vAPI application
        
        ```bash
        git clone https://github.com/roottusk/vapi
        #The collection is in the "postman" folder
        #If you don't have git, you can use:
        sudo apt install git
        ```

    !!! example ""

        ### SQL Injection Lab

        [SQL Injection Lab](https://academy.tcm-sec.com/courses/2008721/lectures/45989264)
        [api-injection.zip](https://cdn.fs.teachablecdn.com/1TJxkxtOQFi21ZlAU5ai)

        Cleaning up your old containers

        ```bash
        #!/bin/bash
        sudo docker stop $(sudo docker ps -aq)
        sudo docker rm $(sudo docker ps -aq)
        sudo docker rmi $(sudo docker images -q)
        sudo docker volume rm $(sudo docker volume ls -q)
        sudo docker network rm $(sudo docker network ls -q)
        ```
        
        Lab troubleshooting

        If you get a general error with one of the labs, e.g. some functionality isn't working try:

        Restarting the lab
        Rebuilding the lab `sudo docker-compose up --build`
        Running the above cleanup script and then rebuilding the lab
        
        If you're not sure what port the lab is running on

        Check the `docker-compose.yml` file. You will see a line similar to "9000:80" so in this case, the lab will be running on `http://localhost:9000`

    !!! example ""

        ### SQL Injection Lab

        [SQL Injection Lab - Login Bypass](https://academy.tcm-sec.com/courses/2008721/lectures/45989643)

        Cleaning up your old containers

        ```bash
        #!/bin/bash
        sudo docker stop $(sudo docker ps -aq)
        sudo docker rm $(sudo docker ps -aq)
        sudo docker rmi $(sudo docker images -q)
        sudo docker volume rm $(sudo docker volume ls -q)
        sudo docker network rm $(sudo docker network ls -q)
        ```
        
        Lab troubleshooting

        If you get a general error with one of the labs, e.g. some functionality isn't working try:

        Restarting the lab
        Rebuilding the lab `sudo docker-compose up --build`
        Running the above cleanup script and then rebuilding the lab
        
        If you're not sure what port the lab is running on

        Check the `docker-compose.yml` file. You will see a line similar to "9000:80" so in this case, the lab will be running on `http://localhost:9000`

    !!! example ""

        ### NoSQL Injection Lab

        [NoSQL Injection Lab](https://academy.tcm-sec.com/courses/2008721/lectures/45990093)
        [api-nosql-injection.zip](https://cdn.fs.teachablecdn.com/194iB1mSPKERWRdB9UaQ)

        Cleaning up your old containers

        ```bash
        #!/bin/bash
        sudo docker stop $(sudo docker ps -aq)
        sudo docker rm $(sudo docker ps -aq)
        sudo docker rmi $(sudo docker images -q)
        sudo docker volume rm $(sudo docker volume ls -q)
        sudo docker network rm $(sudo docker network ls -q)
        ```
        
        Lab troubleshooting

        If you get a general error with one of the labs, e.g. some functionality isn't working try:

        Restarting the lab
        Rebuilding the lab `sudo docker-compose up --build`
        Running the above cleanup script and then rebuilding the lab
        If you're not sure what port the lab is running on

        Check the `docker-compose.yml` file. You will see a line similar to "9000:80" so in this case, the lab will be running on `http://localhost:9000`

    !!! example ""

        ### Mass Assignment Lab

        [Mass Assignment Lab](https://academy.tcm-sec.com/courses/2008721/lectures/45990561)
        [api-mass-assignment.zip](https://cdn.fs.teachablecdn.com/CSomXB0SSFWIxPJyoYAN)

        Cleaning up your old containers

        ```bash
        #!/bin/bash
        sudo docker stop $(sudo docker ps -aq)
        sudo docker rm $(sudo docker ps -aq)
        sudo docker rmi $(sudo docker images -q)
        sudo docker volume rm $(sudo docker volume ls -q)
        sudo docker network rm $(sudo docker network ls -q)
        ```
        
        Lab troubleshooting

        If you get a general error with one of the labs, e.g. some functionality isn't working try:

        Restarting the lab
        Rebuilding the lab `sudo docker-compose up --build`
        Running the above cleanup script and then rebuilding the lab
        If you're not sure what port the lab is running on:

        Check the `docker-compose.yml` file. You will see a line similar to "9000:80" so in this case, the lab will be running on `http://localhost:9000`

    !!! example ""

        Excessive Data Exposure

        Excessive Data Exposure Lab https://academy.tcm-sec.com/courses/2008721/lectures/45990731





