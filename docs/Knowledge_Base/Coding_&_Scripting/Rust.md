!!! info ""

    Rust installation

    ### Windows

    #### Install all needed packages

    ```bash
    rustup uninstall toolchain stable-x86_64-pc-windows-msvc
    rustup toolchain install stable-x86_64-pc-windows-gnu
    rustup default stable-x86_64-pc-windows-gnu
    cargo install jcc-cli
    ```

    ### Linux

    #### Install rust, also installs cargo which is used to run the script

    ```bash
    curl https://sh.rustup.rs -sSf | sh 
    ```

    #### Install the JCC-CLI

    ```bash
    cargo install jcc-cli
    ```
