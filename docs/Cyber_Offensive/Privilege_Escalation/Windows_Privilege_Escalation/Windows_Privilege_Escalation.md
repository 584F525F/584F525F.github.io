!!! info ""

    ### Resources
    - [hacktricks](https://book.hacktricks.xyz/windows-hardening/windows-local-privilege-escalation#system-info)
    - [Windows Kernel Exploits](https://github.com/SecWiki/windows-kernel-exploits)
    - [Privilege Escalation Windows · Total OSCP Guide](https://sushant747.gitbooks.io/total-oscp-guide/content/privilege_escalation_windows.html)
    - [Windows Privilege Escalation Guide](https://www.absolomb.com/2018-01-26-Windows-Privilege-Escalation-Guide/)
    - [PayloadsAllTheThings | Windows Privilege Escalation](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Windows%20-%20Privilege%20Escalation.md)
    - [FuzzySecurity | Windows Privilege Escalation Fundamentals](https://fuzzysecurity.com/tutorials/16.html)

!!! info ""

    ### Tools

    #### Windows Secrets

    - [secretsdump.py](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/secretsdump.py)
    Performs various techniques to dump secrets from the remote machine without executing any agent there. For SAM and LSA Secrets (including cached creds) we try to read as much as we can from the registry and then we save the hives in the target system (%SYSTEMROOT%\Temp directory) and read the rest of the data from there. For DIT files, we dump NTLM hashes, Plaintext credentials (if available) and Kerberos keys using the DL_DRSGetNCChanges() method. It can also dump NTDS.dit via vssadmin executed with the smbexec/wmiexec approach. The script initiates the services required for its working if they are not available (e.g. Remote Registry, even if it is disabled). After the work is done, things are restored to the original state.
    - [mimikatz.py](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/mimikatz.py)
    Mini shell to control a remote mimikatz RPC server developed by @gentilkiwi.


    #### WMI

    - [wmiquery.py:](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/wmiquery.py)
    It allows to issue WQL queries and get description of WMI objects at the target system (e.g. select name from win32_account).
    - [wmipersist.py:](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/wmipersist.py)
    This script creates/removes a WMI Event Consumer/Filter and link between both to execute Visual Basic based on the WQL filter or timer specified.

!!! info ""

    ### Commands

    ##### Initial Enumeration

    ```shell


    ```


