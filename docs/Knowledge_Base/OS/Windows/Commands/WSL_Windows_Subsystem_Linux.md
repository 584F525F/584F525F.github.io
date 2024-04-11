### Kali Linux WSL - [_Reference_](https://www.kali.org/docs/wsl/wsl-preparations/#dism)


Run cmd as Admin

```shell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all
``

Reboot

```shell
wsl --set-default-version 2
```

```shell
wsl --install --distribution kali-linux
#Setup the username and password
```

### Location to move files locally

Change USER_PROFILE

```shell
cd /mnt/c/users/USER_PROFILE/downloads
```
