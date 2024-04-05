??? "df, autoclean & logs"

    ```bash
    df -h
    ```

    Clear log files
    ```bash
    sudo truncate -s 0 /var/log/*log
    ```

    Truncate files using loop
    ```bash
    for logfile in $(ls /var/log/*.log)
    do 
    truncate -s 0 $logfile
    done
    ```

    Check space after
    ```bash
    df -h
    ```

    ```bash
    sudo du -h --max-depth=1 | sort -h
    rm -rf ~/.cache/thumbnails/*
    sudo apt-get autoclean
    sudo apt-get clean
    sudo apt-get autoremove
    ```

    Fill in package name to purge
    ```bash
    sudo apt-get remove --purge <PACKAGENAME>
    ```

??? "Popularity Contest"
    [popularity-contest](https://manpages.debian.org/testing/popularity-contest/popularity-contest.8.en.html)
    ```bash
    sudo apt install popularity-contest
    cd /var/log
    sudo touch popularity-contest
    sudo chmod 666 popularity-contest
    sudo popularity-contest > /var/log/popularity-contest
    popcon-largest-unused
    ```

    Now you can delete packages that are big in size and unused
    ```bash
    sudo apt-get remove --purge <PACKAGENAME>
    ```
