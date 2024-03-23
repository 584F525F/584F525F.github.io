## POP3 

```shell title:POP3 fold:folded
telnet 10.10.45.250 110
#Trying 10.10.45.250...
#Connected to MACHINE_IP.
#Escape character is '^]'.
#+OK MACHINE_IP Mail Server POP3 Wed, 15 Sep 2021 11:05:34 +0300 
USER <frank>
#+OK frank
PASS <D2xc9CgD>
#+OK 1 messages (179) octets
STAT
#+OK 1 179
LIST
#+OK 1 messages (179) octets
1 179
.
RETR 1
#+OK
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
