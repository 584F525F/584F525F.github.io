!!! info ""

    General use to deal with casting issues, using filter source-port and loop-protect

    ```bash
    filter source-port "1" drop 2-23
    filter source-port "2" drop 1,3-23
    filter source-port "3" drop 1-2,4-23
    filter source-port "4" drop 1-3,5-23
    filter source-port "5" drop 1-4,6-23
    filter source-port "6" drop 1-5,7-23
    filter source-port "7" drop 1-6,8-23
    filter source-port "9" drop 1-8,10-23
    filter source-port "10" drop 1-9,11-23
    filter source-port "11" drop 1-10,12-23
    filter source-port "12" drop 1-11,13-23
    filter source-port "13" drop 1-12,14-23
    filter source-port "14" drop 1-13,15-23
    filter source-port "15" drop 1-14,16-23
    filter source-port "16" drop 1-15,17-23
    filter source-port "17" drop 1-16,18-23
    filter source-port "18" drop 1-17,19-23
    filter source-port "19" drop 1-18,20-23
    filter source-port "20" drop 1-19,21-23
    filter source-port "21" drop 1-20,22-23
    filter source-port "22" drop 1-21,23-23
    filter source-port "23" drop 1-22
    
    loop-protect 1-24
    loop-protect 1-24 receiver-action no-disable

    ```

    For a 48 port switch, I would update this to eliminate uplink port from script, unless that works for you.

    ```bash
    filter source-port "1" drop 2-48
    filter source-port "2" drop 1,3-48
    filter source-port "3" drop 1-2,4-48
    filter source-port "4" drop 1-3,5-48
    filter source-port "5" drop 1-4,6-48
    filter source-port "6" drop 1-5,7-48
    filter source-port "7" drop 1-6,8-48
    filter source-port "9" drop 1-8,10-48
    filter source-port "10" drop 1-9,11-48
    filter source-port "11" drop 1-10,12-48
    filter source-port "13" drop 1-12,14-48
    filter source-port "14" drop 1-13,15-48
    filter source-port "15" drop 1-14,16-48
    filter source-port "16" drop 1-15,17-48
    filter source-port "17" drop 1-16,18-48
    filter source-port "18" drop 1-17,19-48
    filter source-port "19" drop 1-18,20-48
    filter source-port "20" drop 1-19,21-48
    filter source-port "21" drop 1-20,22-48
    filter source-port "22" drop 1-21,23-48
    filter source-port "23" drop 1-22,24-48
    filter source-port "24" drop 1-23,25-48
    filter source-port "25" drop 1-24,26-48
    filter source-port "26" drop 1-25,27-48
    filter source-port "27" drop 1-26,28-48
    filter source-port "28" drop 1-27,29-48
    filter source-port "29" drop 1-28,30-48
    filter source-port "30" drop 1-29,31-48
    filter source-port "31" drop 1-30,32-48
    filter source-port "32" drop 1-31,33-48
    filter source-port "33" drop 1-32,34-48
    filter source-port "34" drop 1-33,35-48
    filter source-port "35" drop 1-34,36-48
    filter source-port "36" drop 1-35,37-48
    filter source-port "37" drop 1-36,38-48
    filter source-port "38" drop 1-37,39-48
    filter source-port "39" drop 1-38,40-48
    filter source-port "40" drop 1-39,41-48
    filter source-port "41" drop 1-40,42-48
    filter source-port "42" drop 1-41,43-48
    filter source-port "43" drop 1-42,44-48
    filter source-port "44" drop 1-43,45-48
    filter source-port "45" drop 1-44,46-48
    filter source-port "46" drop 1-45,47-48
    filter source-port "47" drop 1-46,48

    loop-protect 1-48
    loop-protect 1-48 receiver-action no-disable
    ```
    