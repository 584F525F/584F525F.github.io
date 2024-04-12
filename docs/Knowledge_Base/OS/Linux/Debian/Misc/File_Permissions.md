!!! info ""

    The chmod command is used to change the permissions of a file or directory in Linux. The permissions can be represented by a combination of letters (rwx) or by octal numbers (0-7). The octal numbers represent the permissions for the owner, group, and other users, and each number is a combination of the binary values for read, write, and execute permissions.

    The octal numbers for chmod are
    
    ```bash
    7 =rwx (read, write, execute)
    6 =rw- (read, write)
    5 =r-x (read, execute)
    4 =r-- (read only)
    3 =-wx (write, execute)
    2 =-w- (write only)
    1 =--x (execute only)
    0 =--- (no permission)
    ```

    For example, to give read, write, and execute permissions to the owner, read and execute permissions to the group, and execute permission to others

    chmod 751 file.txt
    You can also use the binary representation of each digit to understand the permission better. For example,

    example

    ```bash
    chmod 751 file.txt

    111 (7) is binary representation of 7, first digit represents user permission, so it is 111 (rwx)
    101 (5) is binary representation of 5, second digit represents group permission, so it is 101 (r-x)
    001 (1) is binary representation of 1, third digit represents other permission, so it is 001 (--x)
    ```

    There's a mnemonic that can help you remember these numbers

    ```bash
    rwx rw- r-x r-- -wx -w- --x ---
    
    chmod 7 =rwx
    chmod 6 =rw-
    chmod 5 =r-x
    chmod 4 =r--
    chmod 3 =-wx
    chmod 2 =-w-
    chmod 1 =--x
    chmod 0 =---
    ```
