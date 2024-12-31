!!! info ""

    To Enable PSRemoting

    ```powershell
    Enable-PSRemoting -Force
    ```

    Adding a trusted host

    ```powershell
    winrm s winrm/config/client '@{TrustedHosts="192.5.2.30"}'
    ```

    running commands

    ```powershell
    Invoke-Command -ComputerName WINB -ScriptBlock { echo "Hello World"}
    ```
