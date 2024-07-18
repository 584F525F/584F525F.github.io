!!! info ""

    ### Summary and Commands

    [rfc3501](https://datatracker.ietf.org/doc/html/rfc3501)

    IMAP listens to TCP port 143

    **Basic Commands**

    |Command|Description|
    |:-|:-|
    |telnet <server> 143	|Connect to the IMAP server using Telnet|
    |a login <username> <password>	|Authenticate the user|
    |a select <mailbox>	|Select a mailbox|
    |a examine <mailbox>	|Examine a mailbox|
    |a list "" "*"	|List all available mailboxes|
    |a fetch <message_set> <attribute>	|Fetch message attributes|
    |a store <message_set> <flags>	|Set message flags|
    |a search <charset> <search_criteria>	|Search for messages|
    |a create <mailbox>	|Create a new mailbox|
    |a delete <mailbox>	|Delete a mailbox|
    |a logout	|Log out of the IMAP server|

    **IMAP Operations**

    |Operation	|Description|
    |:-|:-|
    |Connect	|Establish a connection to the IMAP server|
    |Authenticate	|Verify the user’s identity|
    |Select	|Choose a mailbox to work with|
    |Examine	|Inspect the contents of a mailbox|
    |List	|Get a list of available mailboxes|
    |Fetch	|Retrieve message attributes|
    |Store	|Set message flags|
    |Search	|Find messages matching a set of criteria|
    |Create	|Create a new mailbox|
    |Delete	|Remove a mailbox|
    |Logout	|Terminate the session with the server|

    **IMAP Flags**

    |Flag	|Description|
    |:-|:-|
    |\Seen	|The message has been read|
    |\Answered	|The message has been replied to|
    |\Flagged	|The message is flagged for special attention|
    |\Deleted	|The message is marked for deletion|
    |\Draft	|The message is a draft|


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
    USER frank
    #+OK frank
    ```

    ```shell
    PASS D2xc9CgD
    #+OK 1 messages (179) octets
    ```

    ```shell
    STAT
    #+OK 1 179
    ```

    ```shell
    LIST

    #+OK 1 messages (179) octets
    #1 179
    ```

    ```shell
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
