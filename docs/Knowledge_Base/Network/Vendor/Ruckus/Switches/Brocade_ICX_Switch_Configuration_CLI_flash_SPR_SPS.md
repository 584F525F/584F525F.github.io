!!! info ""

    ```bash
    ICX7150-C12 Switch>show flash

    Stack unit 1:
      NAND Type: Micron NAND 2GiB (x 1)
      Compressed Pri Code size = 31457280, Version:08.0.95kT211 (SPS08095k.bin)
      Compressed Sec Code size = 33554432, Version:08.0.95kT213 (SPR08095k.bin)
      Compressed Pri Boot Code size = 786944, Version:10.1.26T225 (mnz10126)
      Compressed Sec Boot Code size = 786944, Version:10.1.26T225 (mnz10126)
      Code Flash Free Space = 1052270592
    ```


    ```bash
    ICX7150-C12 Switch>show version

      Copyright (c) Ruckus Networks, Inc. All rights reserved.
        UNIT 1: compiled on Jun  9 2023 at 06:14:36 labeled as SPS08095k
          (31457280 bytes) from Primary SPS08095k.bin (UFI)
            SW: Version 08.0.95kT211
          Compressed Primary Boot Code size = 786944, Version:10.1.26T225 (mnz10126)
          Compiled on Tue Nov 29 12:43:26 2022

      HW: Stackable ICX7150-C12-POE
    ==========================================================================
    UNIT 1: SL 1: ICX7150-C12-2X10GR POE 12-port Management Module
          Serial  #:ABCDE32U01M
          Software Package: BASE_SOFT_PACKAGE
          Current License: 2X10GR
          P-ASIC  0: type B160, rev 11  Chip BCM56160_B0
    ==========================================================================
    UNIT 1: SL 2: ICX7150-2X1GC 2-port 2G Module
    ==========================================================================
    UNIT 1: SL 3: ICX7150-2X10GF 2-port 20G Module
    ==========================================================================
    1000 MHz ARM processor ARMv7 88 MHz bus
        8 MB boot flash memory
        2 GB code flash memory
        1 GB DRAM
    STACKID 1  system uptime is 1 day(s) 9 hour(s) 3 minute(s) 19 second(s)
    The system started at 06:14:38 GMT+00 Fri Jun 09 2023
    ```

    ```bash
    ICX7150-C12 Switch>enable

    No password has been assigned yet...
    ```

    ```bash
    ICX7150-C12 Switch#boot system flash secondary

    Are you sure? (enter 'y' or 'n'): y
    Could not verify if the Running Config data has been changed.
    Do you want to continue the reload anyway? (enter 'y' or 'n'): y
    ```

    ```bash
    ICX7150-C12 Router#copy flash flash primary

    Flash Memory Write (8192 bytes per dot)
    ICX7150-C12 Router#................
    Processing the bundle image...
    Flashing application image to Primary partition...

    SYNCING IMAGE TO FLASH. DO NOT SWITCH OVER OR POWER DOWN THE UNIT(65536 bytes per dot)...

    Flashing bootrom image to Primary partition...

    SYNCING IMAGE TO FLASH. DO NOT SWITCH OVER OR POWER DOWN THE UNIT(65536 bytes per dot)...
    ............
    Post processing bundle image...
    Bundle image processed successfully

    Copy Done
    ```

    ```bash
    ICX7150-C12 Router#reload
    ICX7150-C12 Router#y
    ICX7150-C12 Router#y
    ```

    ```bash
    CLI>enable
    CLI>show flash
    ```
