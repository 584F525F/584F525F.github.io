!!! info ""

    ### Summary and Commands

    [Simple Mail Transfer Protocol rfc5321](https://www.ietf.org/rfc/rfc5321.txt)
    [Message Submission for Mail rfc6409](https://www.ietf.org/rfc/rfc6409.txt)

    Outgoing email (SMTP) uses port 25

    |Command | Comment|
    |:-|:-|
    |**ATRN**|	Authenticated TURN|
    |**AUTH**|	Authentication|
    |**BDAT**|	Binary data|
    |**BURL**|	Remote content|
    |**DATA**|	The actual email message to be sent. This command is terminated with a line that contains only a|
    |**EHLO**|	Extended HELO|
    |**ETRN**|	Extended turn|
    |**EXPN**|	Expand|
    |**HELO**|	Identify yourself to the SMTP server.|
    |**HELP**|	Show available commands|
    |**MAIL**|	Send mail from email account|
    |**MAIL**| FROM: me@mydomain.com|
    |**NOOP**|	No-op. Keeps you connection open.|
    |**ONEX**|	One message transaction only|
    |**QUIT**|	End session|
    |**RCPT**|	Send email to recipient|
    |**RCPT**| TO: you@yourdomain.com|
    |**RSET**|	Reset|
    |**SAML**|	Send and mail|
    |**SEND**|	Send|
    |**SOML**|	Send or mail|
    |**STARTTLS**	| |
    |**SUBMITTER**|	SMTP responsible submitter|
    |**TURN**|	Turn|
    |**VERB**|	Verbose|
    |**VRFY**|	Verify|


!!! info ""

    ### Example

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
