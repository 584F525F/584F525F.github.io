!!! info ""

    ### C Compiler


    Download and install [Minimalist GNU for Windows](https://sourceforge.net/projects/mingw/files/latest/download)
    - Install
    - continue
    - continue
    - mark for install
        - mingw32-base
        - mingw32-gcc-g++
    - Installation > apply changes > apply

    Edit system environment 
    - user variable
        - edit Path
            - New
                - `c:\MinGW\bin`
    - OK > ok > ok


    In vsCode install Code Runner
    reboot

    ---
    vsCode C/C++ IntelliSense, debugging, and code browsing add on
    [cpptools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)

    ---

    **using the gcc - C compiler**

    ```c
    gcc -fPIC -shared -o shell.so shell.c -nostartfiles
    gcc scriptName -o programName -w
    ```
