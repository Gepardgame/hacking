

## Activate ssh

Under System -> Advanced -> Secure Shell
Activate `Enable Secure Shell` and save

## Routing

Under Firewall -> Rules

Rule to allow everthing from `192.168.1.0/24` to `192.168.2.0/24` in `WAN`
Rule to allow everthing from `192.168.2.0/24` to `192.168.1.0/24` in `LAN`

Under Firewall -> Virtual IP
Add
Type `Proxy ARP`
Interface `LAN`
Address type `Network`
Address `192.168.2.254`

Save

## Disable MRRobot for every ip going through the firewall

Under Firewall -> NAT
Edit second Rule (descrption: allow traffic on port 80 to MrRobot)

Set Destination to `Single Host or Alias` and then the address to `192.168.1.1`