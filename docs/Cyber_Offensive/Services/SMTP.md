!!! info ""

    ```shell
    telnet 10.10.45.250 25
    #Trying 10.10.45.250...
    #Connected to MACHINE_IP.
    #Escape character is '^]'.
    #220 bento.localdomain ESMTP Postfix (Ubuntu)
    ```

    ```shell
    helo telnet
    #250 bento.localdomain
    ```

    ```shell
    mail from: 
    #250 2.1.0 Ok
    ```

    ```shell
    rcpt to: 
    #250 2.1.5 Ok
    ```

    ```shell
    data
    #354 End data with .
    ```

    ```shell
    subject: Sending email with Telnet
    Hello Frank,
    I am just writing to say hi!             
    .
    #250 2.0.0 Ok: queued as C3E7F45F06
    ```

    ```shell
    quit
    #221 2.0.0 Bye
    #Connection closed by foreign host.
    ```
