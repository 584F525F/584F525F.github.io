!!! success ""

    #### install x11vnc

    ```bash
    sudo apt update && sudo apt upgrade -y
    apt install x11vnc
    ```

    #### change user with actual user

    ```bash
    x11vnc storepasswd /home/user/.vnc/passwd
    ```
    Enter password

    ```bash
    mkdir /home/user/.config/autostart
    sudo nano /home/user/.config/autostart/x11vnc.desktop
    ```

    ```bash
    [Desktop Entry]
    Name=X11VNC Server
    Comment=Share this desktop by VNC
    Icon=computer
    Type=Application
    NoDisplay=false
    Hidden=false
    X-GNOME-Autostart-Delay=0
    Exec=x11vnc -ncache 10 -nap -forever -loop -repeat -rfbauth /home/user/.vnc/passwd -rfbport 5900 -noncache display :0 -noxdamage
    ```

    ```bash
    cd /etc/init.d
    sudo nano x11vncscript.sh
    sudo chmod +x x11vncscript.sh
    ```

    #### Write your scrip and save

    ```bash
    sudo x11vnc -ncache 10 -nap -forever -loop -repeat -rfbauth /home/user/.vnc/passwd -rfbport 5900 -noncache display :0 -noxdamage
    ```

    #### Now everytime the OS boots it will run all scripts in the init.d
    To test you can do the following

    ```bash
    cd /etc/init.d
    sudo ./x11vncscript.sh
    ```

    ```bash
    ss -antp | grep vnc
    /usr/share/novnc/utils/novnc_proxy --listen 8081 --vnc localhost:5900
    ```

    You can access it now through your browser
    http://10.10.10.102:8081/vnc.html?host=hostname&port=8081
