!!! info ""

    #### error

    ```bash
    Juni-srx> ssh admin@192.168.161.6

    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    @    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
    @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
    IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
    Someone could be eavesdropping on you right now (man-in-the-middle attack)!
    It is also possible that a host key has just been changed.
    The fingerprint for the RSA key sent by the remote host is
    SHA256:vb3mSzI34f34fId6SkSz/PZwuR072P7sadf43f43f34RhKniE.
    Please contact your system administrator.
    Add correct host key in /var/home/remote/.ssh/known_hosts to get rid of this message.
    Offending RSA key in /var/home/remote/.ssh/known_hosts:4
    RSA host key for 192.168.161.6 has changed and you have requested strict checking.
    Host key verification failed.
    ```

!!! info ""
    
    #### solution
    
    ```bash
    CLI>start shell

    CLI> cat /var/home/remote/.ssh/known_hosts | grep 192.168.161.6

    192.168.161.6 ssh-rsa AAAAB3NzaC1yc2EAAAADAQAyo8s7dfyhsdf96cXN26tB3VMcZ5klCpZVGoP6KJM17DmG47CL6ZP+uusUh0ne2RsUIaZO8WkNXjkqUkVRpKMOVUHJBlmGKE3S+IKXNpSpHNZ1bARTBnsdfsdfirMEcZZ224UcOlheoGidsUMxRL3wzCxFtVBIkufXV1RgC612dl3WTbJC/NxWac3CbrbLZM3FS8eNptiedWpVixNed60XAiYLKL3JYE8FWtgCjkqeiVSSFx8TCh354ga34pxMy25l9P

    CLI> ssh-keygen -f /var/home/remote/.ssh/known_hosts -R "192.168.161.6" 

    # Host 192.168.161.6 found: line 4
    /var/home/remote/.ssh/known_hosts updated.
    Original contents retained as /var/home/remote/.ssh/known_hosts.old
    ```
