!!! info ""

    ### Summary and Commands

    [POP3 RFC 1939](https://www.ietf.org/rfc/rfc1939.txt)

    Incoming email (POP3) uses port 110

    |Command | Comment|
    |:-|:-|
    |USER|	Your user name for this mail server|
    |PASS|	Your password|
    |QUIT|	End your session|
    |STAT|	Number and total size of all messages|
    |LIST|	Message# and size of message|
    |RETR message#|	Retrieve selected message|
    |DELE message#|	Delete selected message|
    |NOOP|	No-op. Keeps you connection open|
    |RSET|	Reset the mailbox. Undelete deleted messages|

    **Normal program flow:**
    USER
    PASS
    LIST
    DELE
    QUIT

!!! info ""

    ### Example

    ```shell
    telnet 10.10.45.250 110

    #Trying 10.10.45.250...
    #Connected to MACHINE_IP.
    #Escape character is '^]'.
    #+OK MACHINE_IP Mail Server POP3 Wed, 15 Sep 2021 11:05:34 +0300 
    ```

    ```shell
    USER <frank>

    #+OK frank
    ```

    ```shell
    PASS <D2xc9CgD>

    #+OK 1 messages (179) octets
    ```

    ```shell
    STAT

    #+OK 1 179
    ```

    ```shell
    LIST

    #+OK 1 messages (179) octets
    ```

    ```shell
    1 179
    .
    RETR 1

    #+OK
    ```

    ```shell
    From: Mail Server 
    To: Frank 
    subject: Sending email with Telnet
    Hello Frank,
    I am just writing to say hi!
    .
    QUIT

    #+OK MACHINE_IP closing connection
    #Connection closed by foreign host.
    ```
