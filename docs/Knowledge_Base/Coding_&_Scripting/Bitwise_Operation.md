!!! info ""

    Example Binary numbers

    ```bash
    3    = 000011
    5    = 000101
    10   = 001010
    ```
 
    #### Bitwise AND

    Take two numbers, line them up on top of each other, and create a new number that has a 1 where both numbers have a 1 (everything else is 0).

    ```bash
      3          =>  00011
    & 5          =>  00101
    ----           -------
    1                00001
    ```

    #### Bitwise OR

    Take two numbers, line them up on top of each other, and create a new number that has a 1 where either number has a 1 (everything else is 0).

    ```bash
      3          =>  00011
    | 5          =>  00101
    ----           -------
    7                00111
    ```

    #### Bitwise NOR (Not OR)

    Take the Bitwise OR of two numbers, and then reverse everything (where there was a 0, there's now a 1, where there was a 1, there's now a 0)

    ```bash
    # simplified gate view ^(3|5)

    ^
    ( 3           =>  00011
    | 5)          =>  00101
    ----           -------
    6                 11000 
    ```

    #### Bitwise XOR (exclusive OR)

    Take two numbers, line them up on top of each other, and create a new number that has a 1 where either number has a 1 AND the other number has a 0 (everything else is 0).

    ```bash
      3          =>  00011
    ^ 5          =>  00101
    ----           -------
    6                00110 
    ```

    #### Bitwise NAND (Not AND)

    Take the Bitwise AND of two numbers, and then reverse everything (where there was a 0, there's now a 1, where there was a 1, there's now a 0).

    ```bash
        n          =>  abcdefghjikl
    &   15         =>  000000001111
    ------            --------------
        ?              00000000jikl
    ```

    #### Bitshift Operator

    means "shift everything left n bits" or "shift everything right n bits"

    ```bash
    1 << 3 = 0001 << 3 = 0001000 = 8

    And:

    8 >> 2 = 01000 >> 2 = 010 = 2
    ```


!!! info ""

    #### Truth table for all binary logical operators

    ![alt text](/Knowledge_Base/images/bitwise_img_0.png)

!!! info ""

    [Online Base Convertor](https://www.convertit.com/go/convertit/calculators/math/base_converter.asp)
