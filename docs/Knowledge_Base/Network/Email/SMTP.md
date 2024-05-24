!!! info ""

    Simple Mail Transfer Protocol (SMTP) - **Send email**

    ### Email components

    **Email delivery over the Internet requires the following components:**
    1. Mail Submission Agent (MSA)
    2. Mail Transfer Agent (MTA)
    3. Mail Delivery Agent (MDA)
    4. Mail User Agent (MUA)

    ![alt text](/Knowledge_Base/images/SMTP-822a449fd569c16c875a13ca2487b714.png)

    **The figure shows the following five steps that an email needs to go through to reach the recipient’s inbox:**
       
    5. <mark>A Mail User Agent (MUA) or simply an email client</mark> connects to a <mark>Mail Submission Agent (MSA)</mark> to send it a user's email.
    6. The <mark>MSA</mark> receives the message, <mark>checks for any errors before transferring it to the Mail Transfer Agent (MTA) server</mark>, commonly hosted on the same server.
    7. The <mark>MTA will send the email message to the MTA of the recipient</mark>, The MTA can also function as a Mail Submission Agent (MSA).
    8. A typical setup would have the MTA server also functioning as a Mail Delivery Agent (MDA).
    9. The <mark>recipient will collect its email from the MDA using their email client</mark>.


    **In the same way, we need to follow a protocol to communicate with an HTTP server, and we need to rely on email protocols to talk with an MTA and an MDA. The protocols are:**
    1. Simple Mail Transfer Protocol (SMTP)
    2. Post Office Protocol version 3 (POP3) or Internet Message Access Protocol (IMAP)

    Simple Mail Transfer Protocol (SMTP) is used to communicate with an MTA server. Because SMTP uses cleartext, where all commands are sent without encryption, we can use a basic Telnet client to connect to an SMTP server and act as an email client (MUA) sending a message.

    SMTP server listens on port 25 by default. To see basic communication with an SMTP server, we used Telnet to connect to it. Once connected, we issue `helo hostname` and then start typing our email.

    ```bash
    telnet 10.10.45.250 25
    #Trying 10.10.45.250...
    #Connected to MACHINE_IP.
    #Escape character is '^]'.
    #220 bento.localdomain ESMTP Postfix (Ubuntu)
    helo telnet
    #250 bento.localdomain
    mail from: 
    #250 2.1.0 Ok
    rcpt to: 
    #250 2.1.5 Ok
    data
    #354 End data with .
    subject: Sending email with Telnet
    Hello Frank,
    I am just writing to say hi!             
    #.
    #250 2.0.0 Ok: queued as C3E7F45F06
    quit
    #221 2.0.0 Bye
    #Connection closed by foreign host.
    ```

    After `helo`, we issue `mail from:`, `rcpt to:` to indicate the sender and the recipient. When we send our email message, we issue the command `data` and type our message. We issue `<CR><LF>.<CR><LF>` (or `Enter . Enter` to put it in simpler terms). The SMTP server now queues the message.

    Generally speaking, we don’t need to memorize SMTP commands. The console output above aims to help better explain what a typical mail client does when it uses SMTP.


!!! info ""

    ### Mail Agents 

    There are four main agents: 

    - <mark>**MUA**</mark> (Mail User Agent) is the email client we mentioned above. It’s an application or a website that you use to send and receive email messages.
    - <mark>**MSA**</mark> (Mail Submission Agent) receives emails from the email client, checks its headers, and verifies that the addresses are indicated correctly. 
    - [<mark>**MTA**</mark>](https://mailtrap.io/blog/mail-transfer-agent/) (Mail Transfer Agent) is a sendmail program that processes and transfers emails. It receives messages from the MSA. Most modern MTAs take on MSA’s responsibilities. In that case, message transfer won’t include MSAs. The most popular MTAs are Sendmail, Postfix, and Exim.
    - <mark>**MDA**</mark> (Mail Delivery Agent) is the final agent before your emails get delivered to the recipient’s SMTP server and then retrieved through inbound email servers (IMAP or POP3).

    ![alt text](/Knowledge_Base/images/SMTP-20231231234938.png)

    ![alt text](/Knowledge_Base/images/SMTP-20231231234916.png)

    ![alt text](/Knowledge_Base/images/SMTP-20231231235130.png)

    ![alt text](/Knowledge_Base/images/SMTP-20231231234814.png)

    ![alt text](/Knowledge_Base/images/SMTP-20231231234602.png)
