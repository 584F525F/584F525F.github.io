!!! info ""

    Linux Bash script to check directoy file * PEM and will print cert end date

    ```shell
    for pem in /etc/ssl/certs/*.pem; do
    printf '%s: %s\\n' \\
    "$(date --date="$(openssl x509 -enddate -noout -in "$pem"|cut -d= -f 2)" --iso-8601)" \\
    "$pem"
    done | sort
    ```
