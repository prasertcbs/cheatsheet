# ssh public key authentication

## Windows 10
```
where.exe ssh-keygen
```

## ssh-keygen
```sh
# default on Windows 10 OpenSSH
ssh-keygen
ssh-keygen -t rsa -b 3072
ssh-keygen -t rsa -b 4096

# recommended
ssh-keygen -t ed25519
```

## copy public key to server
```
local> ssh user@host
remote> mkdir -p ~/.ssh

local> scp ~/.ssh/id_rsa.pub user@host:~/.ssh/authorized_keys

# Windows
local> cd ~\.ssh
local> scp id_rsa.pub user@host:~/.ssh/authorized_keys

remote> chmod 600 ~/.ssh/authorized_keys
```

## scp
```
scp demo.txt simba@192.168.1.200:~/Documents
```

## sftp
```
sftp mx
```

## .ssh/config
```
Host mx
  HostName 192.168.1.200
  User simba
  Port 22

Host ivy
  HostName 192.168.1.66
  User prasert
  Port 22
```

## connection using ~/.ssh/config
```
ssh mx
sftp mx
scp demo.txt mx:~/Documents
```

