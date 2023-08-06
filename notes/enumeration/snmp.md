### Enumerate Simple Network Manager Protocol Servers with onesixtyone

```bash
echo public > community
echo private >> community
echo manager >> community
for ip in $(seq 1 254); do echo 10.11.1.$ip; done > ips
onesixtyone -c community -i ips
```

Alternatively with Nmap:
`sudo nmap -sU --open -p161 <Target IP> -oG open-snmp.txt`

Tree-like structure under the SNMP Management Information Base (MIB). Branches represent organisations or network functions, leaves correspond to specific variable values that a user may query. Said values are a potentially rich source of information with more than just network information container within.

### Traverse MIB with snmpwalk

`snmpwalk -c <Community> -v<Version> -t <Timeout> <Target IP>`
from exercises:
`snmpwalk -c public -v1 -t 10 192.168.50.151`
snmpwalk can be used more precisely by passing specific OIDs, for Windows users:
`snmpwalk -c <Community> -v<Version> <Target IP> 1.3.6.1.4.1.77.1.2.25`
and for running processes:
`snmpwalk -c <Communtiy> -v<Version> <Target IP> 1.3.6.1.2.1.25.4.2.1.2`
installed software:
`snmpwalk -c <Communtiy> -v<Version> <Target IP> 1.3.6.1.2.1.25.6.3.1.2`
listening TCP ports:
`snmpwalk -c <Communtiy> -v<Version> <Target IP> 1.3.6.1.2.1.6.13.1.3`