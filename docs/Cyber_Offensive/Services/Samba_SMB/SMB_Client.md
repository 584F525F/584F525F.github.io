!!! info ""

    #### get list of shares on target

    ```shell
    smbclient -L //10.10.0.50/
    ```

    #### if it was misconfigured, we can log in anonymously by simply hitting _Enter_ at the prompt

    ```shell
    #-U flag to specify the username (in this case a blank string) and the -N flag to specify no password
    smbclient -L //10.10.0.50/ -U '' -N
    ```

    #### connect to share name

    ```shell
    smbclient //10.10.0.50/<sharename>
    ```

    #### list directory

    ```shell
    dir
    ```

    #### download file

    ```shell
    get example.txt
    ```

    #### upload file

    ```shell
    put evil_file.txt
    ```
