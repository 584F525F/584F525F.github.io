??? "curl"

    ##### curl Version
    ```bash
    curl -V          
    curl --version
    ```

    ##### Download
    ```bash
    The 'curl -O' option will save the file name the same as in the URL only
    The 'curl -o' option can choose a different name to save the output file
    ```
    curl -O https://xxxx/xxx.gz
    curl -o zzz.gz https://zzz/zzz.gz
    ```

    ##### Download multiple files
    ```bash
    curl -O https://xxxx/xxxx.gz -O https://xxxx/xxxx.gz
    ```

    ##### Continue from inturrupted download
    ```bash
    curl -C - -O https://xxxxx/xxxxx.gz
    ```

    ##### Download from FTP & SFTP
    ###### Normal FTP
    ```bash
    curl -u FTP_UserName:FTP_Password -O ftp://xxx/README.txt
    ```

    ###### For SFTP
    ```bash
    curl -u SFTP_UserName:SFTP_Password -O -k sftp://xxx/README.txt
    ```

    ##### Upload file FTP & SFTP
    ```bash
    -T flag represents the upload file.
    -k flag used in SFTP explicitly allows curl to perform "insecure" SSL connections and transfers.
    ```

    ###### Normal FTP:
    ```bash
    curl -u FTP_UserName:FTP_Password -T linuxteck.sql.gz ftp://linuxteck.com
    ```

    ###### For SFTP :
    ```bash
    curl -u SFTP_UserName:SFTP_Password -T -k sftp://linuxteck.com/README.txt
    ```

    ##### Delete file from FTP
    ```bash
    curl ftp://xxxxx -X 'DELE xxxx.gz' -u FTP_UserName:FTP_Password
    ```

    ##### Transfer using proxy
    ```bash
    curl -x proxy.example.com:3128 -O https://xxxx/abc.html
    ```
