!!! example ""

    ## Rust Method

    !!! info ""

        ### Windows

        #### Install all needed packages

        ```bash
        rustup uninstall toolchain stable-x86_64-pc-windows-msvc
        rustup toolchain install stable-x86_64-pc-windows-gnu
        rustup default stable-x86_64-pc-windows-gnu
        cargo install jcc-cli
        ```

        #### Clone the repository

        ```bash
        git clone https://github.com/584F525F/juniper-config-converter.git
        ```

        #### Enter the `juniper-config-converter` directory

        ```bash
        cd juniper-config-converter
        ```

        #### Copy your Juniper configuration file into this directory

        Copy the Juniper configuration file into this directory, you can rename it to 'juniper_test.txt'

        #### start the conversion process

        ```bash
        jcc-cli --file juniper_test.txt
        ```
        You should get the result of the conversion almost immediately.

    !!! info ""
        
        ### Linux

        #### Install rust, also installs cargo which is used to run the script

        ```bash
        curl https://sh.rustup.rs -sSf | sh 
        ```

        #### Install the JCC-CLI

        ```bash
        cargo install jcc-cli
        ```

        #### Clone the repository

        ```bash
        git clone https://github.com/584F525F/juniper-config-converter.git
        ```

        #### Run the script and pass your juniper config file parameter to it

        ```bash
        jcc-cli --file juniper_test.txt
        ```

!!! example ""

    ## Python Method juniper_display_set

    #### Clone the repository

    ```bash
    git clone https://github.com/584F525F/juniper_display_set.git
    ```

    #### Enter the juniper_display_set directory

    ```bash
    cd juniper_display_set
    ```

    #### Execute the script by providing the input configuration file and redirecting the output to a new file
    
    ```bash
    python3 junos_converter.py --input ../sample_config.cfg > sample_config_set.set
    
    ```
    If you check the new file, it will have the set config

!!! example ""

    ## Using another Juniper Method

    you can always use any (similar) Juniper device and do

    ```bash
    configure
    load override terminal
    #paste your config
    <Crtl-D>
    show | display set
    rollback
    exit
    ```
