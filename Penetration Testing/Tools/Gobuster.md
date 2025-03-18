### Enumerate directorys
```bash
gobuster dir -u $url -w $wordlist 
```

Good wordlist `/usr/share/dirbuster/wordlists/directory-list-2.3-medium.txt`

### Enumerate file based on file endings
add `-x $endings` to gobuster like that `-x php,txt,html`