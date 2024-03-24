```shell
# Show hidden options
./john --list=hidden-options

# Using session and restoring them
./john hashes --session=name
./john --restore=name
./john --session=allrules --wordlist=all.lst --rules mypasswd &
./john status

# Show the potfile
./john hashes --pot=potFile --show

# Search if a root/uid0 have been cracked
john --show --users=0 mypasswdFile
john --show --users=root mypasswdFile

# List OpenCL devices and get their id
./john --list=opencl-devices

# List format supported by OpenCL
./john --list=formats --format=opencl

# Using multiples GPU
./john hashes --format:openclformat --wordlist:wordlist --rules:rules --dev=0,1 --fork=2

# Using multiple CPU (eg. 4 cores)
./john hashes --wordlist:wordlist --rules:rules --dev=2 --fork=4
```