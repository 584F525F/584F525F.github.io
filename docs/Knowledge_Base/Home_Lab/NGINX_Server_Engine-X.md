!!! info ""

    pronounced as “Engine-X”
    [Install and configure Nginx | Ubuntu](https://ubuntu.com/tutorials/install-and-configure-nginx#1-overview)


    #### Installing Nginx
    
    ``` bash
    sudo apt update
    sudo apt install nginx -y

    cd /var/www
    sudo mkdir tutorial
    cd tutorial
    sudo "${EDITOR:-nano}" index.html
    ```

    #### Creating our own website
    Paste the following to the `index.html` file:
    
    ```html
    <!doctype html>
    <html>
    <head>
        <meta charset="utf-8">
        <title>Hello, Nginx!</title>
    </head>
    <body>
        <h1>Hello, Nginx!</h1>
        <p>We have just configured our Nginx web server on Ubuntu Server!</p>
    </body>
    </html>
    ```

    #### Setting up virtual host
    
    ```bash
    cd /etc/nginx/sites-enabled
    sudo "${EDITOR:-nano}" tutorial
    ```

    `root` is a directory where we have placed our .html file. `index` is used to specify file available when visiting root directory of site. `server_name` can be anything you want, because you aren’t pointing it to any real domain by now.
    
    ```html
    server {
        listen 5895;
        listen [::]:5895;

        server_name example.ubuntu.com;

        root /var/www/tutorial;
        index index.html;

        location / {
                try_files $uri $uri/ =404;
        }
    }
    ```

    #### Activating virtual host and testing results

    ```bash
    sudo service nginx restart
    ```
