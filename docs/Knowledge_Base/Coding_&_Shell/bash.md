!!! info ""

    #### For-loops

    ```
    #!/bin/bash

    for ((i = 0; i < 10; i++)); do
        echo $i
    done
    ```

    Another way to write this is by using the program `seq`. Seq is pretty much like `range()` in python. So it can be used like this:

    ```
    #!/bin/bash

    for x in `seq 1 100`; do
        echo $x
    done
    ```

    #### If statement

    `$1` here represent the first argument.

    ```

    if [ "$1" == "" ]; then
        echo "This happens"
    fi
    ```

    #### If/Else

    ```
    #!/bin/bash

    if [ "$1" == "" ]; then
        echo "This happens"
    else
        echo "Something else happens"
    fi
    ```

    #### Command line arguments

    Command line arguments are represented like this

    ```
    #!/bin/bash

    $1
    ```

    This is the first command line argument.

    #### Daemonize an execution

    If you do a ping-sweep with host the command will take about a second to complete. And if you run that against 255 hosts I will take a long time to complete. To avoid this we can just deamonize every execution to make it faster. We use the `&` to daemonize it.

    ```
    #!/bin/bash

    for ip in $(cat ips.txt); do
        ping -c 1 $ip &
    done
    ```
