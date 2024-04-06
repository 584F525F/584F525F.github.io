
#### runs all options apart from dictionary based share name guessing
```shell
enum4linux -a target-ip
```

#### list usernames
```shell
enum4linux -U x.x.x.x
```

#### list windows shares
```shell
enum4linux -S x.x.x.x
```

#### dictionary attack
```shell
enum4linux -s shares.txt target-ip
```

#### pull usernames from the default RID range (500-550,1000-1050)
```shell
enum4linux -r target-ip
```

#### pull usernames using a custom RID range
```shell
enum4linux -R 600-660 target-ip
```
#### view password policy
```shell
enum4linux -P x.x.x.x
```

#### view OS info
```shell
enum4linux -o x.x.x.x
```

#### list groups
```shell
enum4linux -G target-ip
```

#### if on domain, tried to get some LDAP info
```shell
enum4linux -l x.x.x.x
```

#### -i flag any Printer info
```shell
enum4linux -i x.x.x.x
```

#### NetBIOS info
```shell
enum4linux -n x.x.x.x
```

#### run all simple enumeration
```shell
enum4linux -a x.x.x.x
```

#### connect with user and password
```shell
enum4linux -u administrator -p password -U target-ip
```

#### verbose mode
```shell
enum4linux -v target-ip
```