### Enumerate directorys
```bash
gobuster dir -u $url -w $wordlist 
```

Good wordlist ```
```path
/usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt
```

#### Enumerate file based on file endings
add `-x $endings` to gobuster like [[CheatSheet]]that `-x php,txt,html`

### Enumerate Subdomains
```bash
gobuster dns -d $domain -w $wordlist
```

Good wordlist ```
```path
/usr/share/seclists/Discovery/DNS/namelist.txt
```