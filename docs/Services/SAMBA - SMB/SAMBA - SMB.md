## Samba enumeration

```shell
#everything, runs all options apart from dictionary based share name guessing
enum4linux -a target-ip

#list usernames
enum4linux -U x.x.x.x

#list windows shares
enum4linux -S x.x.x.x

#dictionary attack
enum4linux -s shares.txt target-ip

#pull usernames from the default RID range (500-550,1000-1050)
enum4linux -r target-ip

#pull usernames using a custom RID range
enum4linux -R 600-660 target-ip

#view password policy
enum4linux -P x.x.x.x

#view OS info
enum4linux -o x.x.x.x

#list groups
enum4linux -G target-ip

#if on domain, tried to get some LDAP info
enum4linux -l x.x.x.x

#-i flag any Printer info
enum4linux -i x.x.x.x

#NetBIOS info
enum4linux -n x.x.x.x

#run all simple enumeration
enum4linux -a x.x.x.x

#connect with user and password
enum4linux -u administrator -p password -U target-ip

#verbose mode
enum4linux -v target-ip
```

## SMB Client

```shell
#get list of shares on target
smbclient -L //10.10.0.50/

#if it was misconfigured, we can log in anonymously by simply hitting _Enter_ at the prompt
#-U flag to specify the username (in this case a blank string) and the -N flag to specify no password
smbclient -L //10.10.0.50/ -U '' -N

#connect to share name
smbclient //10.10.0.50/<sharename>

#list directory
dir

#download file
get example.txt

#upload file
put evil_file.txt
```

## SMB/MSRPC

[smbclient.py](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/smbclient.py) 
- A generic SMB client that will let you list shares and files, rename, upload and download files and create and delete directories, all using either username and password or username and hashes combination. It’s an excellent example to see how to use impacket.smb in action.

[addcomputer.py](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/addcomputer.py)
- Allows to add a computer to a domain using LDAP or SAMR (SMB).

[getArch.py:](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/getArch.py) 
- This script will connect against a target (or list of targets) machine/s and gather the OS architecture type installed by (ab)using a documented MSRPC feature.

[exchanger.py](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/exchanger.py)
- A tool for connecting to MS Exchange via RPC over HTTP v2.

[lookupsid.py:](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/lookupsid.py) 
- A Windows SID brute forcer example through [MS-LSAT] MSRPC Interface, aiming at finding remote users/groups.

[netview.py:](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/netview.py) 
- Gets a list of the sessions opened at the remote hosts and keep track of them looping over the hosts found and keeping track of who logged in/out from remote servers.

[reg.py:](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/reg.py) 
- Remote registry manipulation tool through the [MS-RRP] MSRPC Interface. The idea is to provide similar functionality as the REG.EXE Windows utility.

[rpcdump.py:](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/rpcdump.py) 
- This script will dump the list of RPC endpoints and string bindings registered at the target. It will also try to match them with a list of well known endpoints.

[rpcmap.py](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/rpcmap.py)
- Scan for listening DCE/RPC interfaces. This binds to the MGMT interface and gets a list of interface UUIDs. If the MGMT interface is not available, it takes a list of interface UUIDs seen in the wild and tries to bind to each interface.

[samrdump.py:](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/samrdump.py) 
- An application that communicates with the Security Account Manager Remote interface from the MSRPC suite. It lists system user accounts, available resource shares and other sensitive information exported through this service.

[services.py:](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/services.py) 
- This script can be used to manipulate Windows services through the [MS-SCMR] MSRPC Interface. It supports start, stop, delete, status, config, list, create and change.

[smbpasswd.py](https://github.com/SecureAuthCorp/impacket/blob/impacket_0_10_0/examples/smbpasswd.py)
- This script is an alternative to smbpasswd tool and intended to be used for changing expired passwords remotely over SMB (MSRPC-SAMR)
