!!! info ""

    #### For-loops

    ```bash
    #!/bin/bash

    for ((i = 0; i < 10; i++)); do
        echo $i
    done
    ```

    Another way to write this is by using the program `seq`. Seq is pretty much like `range()` in python. So it can be used like this:

    ```bash
    #!/bin/bash

    for x in `seq 1 100`; do
        echo $x
    done
    ```

    #### If statement

    `$1` here represent the first argument.

    ```bash
    if [ "$1" == "" ]; then
        echo "This happens"
    fi
    ```

    #### If/Else

    ```bash
    #!/bin/bash

    if [ "$1" == "" ]; then
        echo "This happens"
    else
        echo "Something else happens"
    fi
    ```

    #### Command line arguments

    Command line arguments are represented like this

    ```bash
    #!/bin/bash

    $1
    ```

    This is the first command line argument

    #### Daemonize an execution

    If you do a ping-sweep with host the command will take about a second to complete. And if you run that against 255 hosts I will take a long time to complete. To avoid this we can just deamonize every execution to make it faster. We use the `&` to daemonize it.

    ```bash
    #!/bin/bash

    for ip in $(cat ips.txt); do
        ping -c 1 $ip &
    done
    ```

    #### Use the output of command

    It has happened to me several times that I want to input the output of a command into a new command, for example:

    I search for a file, find three, and take the last line, which is a path. Now I want to cat that path:

    ```bash
    #!/bin/bash

    locate 646.c | tail -n 1
    ```

    This can be done like this:

    ```bash
    #!/bin/bash

    cat $(locate 646.c | tail -n 1)
    ```


    #### picoCTF flag save

    ```bash
    #Create script with below
    #File save.sh and chmod +x
    #!/bin/bash
    original_directory=$(pwd)
    cd ..
    mv $original_directory ${original_directory}_COMPLETED

    #run as follows
    source script.sh

    #save flag script
    #!/bin/bash
    winning_command=$(history | tail -n 1 | cut -b 8-)

    #Create a new script within this script to pass the value of winning_command
    #EOF > End of file
    cat <<EOF>./get_flag.sh
    #!/bin/bash
    ${winning_command}
    EOF

    chmod +x get_flag.sh
    get_flag.sh > flag.txt

    Running the above must be done after obtaining the flag
    run the command .\run | grep -oE "picoCTF{.*}" --color=none
    Run only the save.sh
    Now that would have created a get_flag.sh and a flag.txt
    you can cat the txt file for the flag
    ```

    ## Iterate over a file

    This script will iterate over a file and echo out every single line

    ```bash
    #!/bin/bash

    for line in $(cat file.txt);do
        echo $line
    done
    ```

    Another way of writing is this

    ```bash
    #!/bin/bash

    while read p; do
        echo  $p
    done <file.txt
    ```
