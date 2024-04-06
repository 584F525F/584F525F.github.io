    ??? "Change your timezone you can use"
    ### Change your timezone you can use
    ```bash
    sudo dpkg-reconfigure tzdata
    ```

    ??? "Update the time and date from the internet"
    ### Update the time and date from the internet
    ```bash
    timedatectl set-ntp true
    ```


??? "Alternative NTP"
    ### Alternative NTP
    
    #### Install
    If `ntpd` is not installed use one of the following command to install `ntpd`
    ```bash
    sudo apt-get install ntp
    ```

    #### Configuration
    You should at least set following parameter in `/etc/ntp.conf` config file
    ```bash
    server <Time Server Name or IP Address>
    ```

    For example, open `/etc/ntp.conf` file using vi text editor
    ```bash
    vi /etc/ntp.conf
    ```

    Locate server parameter and set it as follows
    ```bash
    server pool.ntp.org
    ```

    Save the file and restart the `ntpd` service
    ```bash
    /etc/init.d/ntpd start
    ```

    You can synchronize the system clock to an NTP server immediately with following command
    ```bash
    ntpdate pool.ntp.org
    ```

??? "Manually setting the date"
    ### Manually setting the date

    For setting the time and date manually use the following syntax
    ```bash
    date --set="STRING"
    ```

    For example, to set the date to `2 Oct 2006 18:00:00`, type the following command as root user
    ```bash
    date -s "2 OCT 2006 18:00:00"
    ```

    OR
    ```bash
    date --set="2 OCT 2006 18:00:00"
    ```

    You can also simplify format using following syntax
    ```bash
    date +%Y%m%d -s "20081128"
    ```

    To set time use the following syntax
    ```bash
    date +%T -s "10:13:13"
    ```

    where:

    - `10`: Hour (hh)
    - `13`: Minute (mm)
    - `13`: Second (ss)

    You can use `%p` for the locale's equivalent of AM/PM
    ```bash
    date +%T%p -s "6:10:30AM"
    date +%T%p -s "12:10:30PM"
    ```
