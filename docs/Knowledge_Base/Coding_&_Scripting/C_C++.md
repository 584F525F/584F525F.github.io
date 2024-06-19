!!! info ""

    !!! info ""

        ### C Compiler Windows install

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


        - In vsCode install [C/C++ Runner](https://marketplace.visualstudio.com/items?itemName=franneck94.c-cpp-runner) extension
        - In vsCode install [cpptools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools)
        - reboot

    !!! info ""

        ### Windows Environment Variables

        Edit Windows Environment Variables
        User Variables
        Add new
        `C:\msys64\ucrt64\bin`
        Click ok

        ```bash
        #open cmd and run the following
        gcc --version
        g++ --version
        gdb --version
        ```


    !!! info ""

        ### using the gcc - C compiler

        ```c
        gcc -fPIC -shared -o shell.so shell.c -nostartfiles
        gcc scriptName -o programName -w
        ```


!!! info ""

    ### Arch Linux - C++ and MinGW-w64 in Visual Studio Code

    [Get Started with C++ and MinGW-w64 in Visual Studio Code](https://code.visualstudio.com/docs/cpp/config-mingw)
    Download and install the exe from [MSYS2](https://www.msys2.org/)
    
    In the window after installation run the following

    ```bash
    pacman -S mingw-w64-ucrt-x86_64-gcc
    pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain
    ```




!!! info ""

    ### Learning Resources

    - [learn-c](https://www.learn-c.org/)
