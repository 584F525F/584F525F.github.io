!!! info ""

    Installing VNC

    ```bash
    sudo apt update
    sudo apt install -y tightvncserver
    ```

    To complete the VNC server’s initial configuration after installation, use the vncserver command to set up a secure password and create the initial configuration files:

    ```bash
    sudo vncserver
    ```

    You’ll be prompted to enter and verify a password to access your machine remotely

    **example**

    ```bash
    ->$ sudo vncserver
    [sudo] password for batman:

    You will require a password to access your desktops.

    Password:
    Verify:
    Would you like to enter a view-only password (y/n)? n

    Warning: batman:1 is taken because of /tmp/.X1-lock
    Remove this file if there is no X server batman:1
    xauth:  file /root/.Xauthority does not exist

    New 'X' desktop is batman:6

    Creating default startup script /root/.vnc/xstartup
    Starting applications specified in /root/.vnc/xstartup
    Log file is /root/.vnc/batman:6.log
    ```

!!! info ""

    Only if needed - update [nano ./.vnc/xstartup] with below

    ```bash
    !/bin/sh
    # Uncomment the following two lines for normal desktop:
    # unset SESSION_MANAGER
    # exec /etc/X11/xinit/xinitrc
    unset DBUS_SESSION_BUS_ADDRESS
    xrdb $HOME/.Xresources
    xsetroot -solid grey
    # vncconfig -iconic &
    # x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
    /etc/X11/Xsession &
    export XKL_XMODMAP_DISABLE=1
    exec /usr/bin/mate-session &
    ```
