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
    filter source-port "13" drop 1-12,14-23
    filter source-port "14" drop 1-13,15-23

    loop-protect 1-24
    loop-protect 1-24 receiver-action no-disable

    ```
