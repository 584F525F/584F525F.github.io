

??? "Find file in specific location"
    ### Find file in specific location
    Change location /opt/
    Change what you are searching for, file name "go.d.plugin”
    ```bash
    sudo find -O3 -L /opt/ -name "go.d.plugin”
    ```


??? "Using grep to find txt in files"
    ### Using grep to find txt in files

    #### Search for word in file
    For case insensitive use -i
    ```bash
    grep WORD file.txt
    ```

    #### Search case insensitive Word in file type
    ```bash
    grep -i WORD *.txt
    ```

    #### Search case insensitive Word in ANY file type
    ```bash
    grep -i WORD *
    ```

    #### RECURSION
    ```bash
    -r, --recursive
            Read all files under each directory, recursively, following symbolic  links only if they are on the command line.
            Note that if no file operand is given, grep searches the working directory.  This is equivalent to the -d recurse option.

    -R, --dereference-recursive
            Read  all  files under each directory, recursively. Follow all symbolic links, unlike -r.
    ```

    ##### Search recursively for word starting current directory
    ```bash
    grep -r Word .
    ```

    ##### For case insensitive
    ```bash
    grep -ir Word .
    ```

    ##### Search recursively for word starting in a specific directory
    ```bash
    grep -r Word /path..
    ```

    ##### For case insensitive
    ```bash
    grep -ir Word /path..
    ```

    ##### Search recursively for word starting current directory and in a specific file type
    ```bash
    grep -ir --include="*.txt" Word .
    ```

    ##### Search recursively for sentence starting current directory 
    ```bash
    grep -ri "Word after word" .
    ```

??? "Using Locate"
    ### Using Locate
    ```bash
    locate file_name
    updatedb
    ```
