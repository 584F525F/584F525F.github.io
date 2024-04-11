
```powershell
get-childitem * -r | foreach {rename-item $_ $_.name.replace("-opendir.cloud","")}
```
