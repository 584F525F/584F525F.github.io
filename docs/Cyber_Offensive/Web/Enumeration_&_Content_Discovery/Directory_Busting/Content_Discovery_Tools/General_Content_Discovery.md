!!! info ""

    #### We can use the favicon link of a website to find the framework used
    ```shell
    curl https://website.com/favicon.ico | md5sum
    #this calculates md5 hash value after downloading the favicon
    #hash can be used to lookup on <https://wiki.owasp.org/index.php/OWASP_favicon_database>
    ```

    #### Manually discovering HTTP headers
    ```shell
    curl http://website.com/ -v
    ```
