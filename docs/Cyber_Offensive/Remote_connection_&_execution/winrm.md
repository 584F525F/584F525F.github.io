!!! info ""

    ```powershell
    #To Enable PSRemoting
    Enable-PSRemoting -Force

    #Adding a trusted host
    winrm s winrm/config/client '@{TrustedHosts="192.5.2.30"}'

    #running commands
    Invoke-Command -ComputerName WINB -ScriptBlock { echo "Hello World"}
    ```
