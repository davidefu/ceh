# Sniffing

## Perform active sniffing

- Perform MAC flooding using macof
macof -i eth0 -n 10
macof -i eth0 -d [Target IP Address]

- Perform a DHCP starvation attack using Yersinia
yersinia -I
F2 -> DHCP mode --> STP Fields change to DHCP Fields
1 --> DHCP starvation attack

- Perform ARP poisoning using arpspoof
arpspoof -i eth0 -t 10.10.1.1 10.10.1.11

- Perform an Man-in-the-Middle (MITM) attack using Cain & Abel
windows software
click on Configure
Sniffer tab --> click on + --> Scan MAC Addresses
ARP tab at the bottom
New ARP Poison Routing
made some ftp connection
Passwords tab at the bottom

- Spoof a MAC address using TMAC and SMAC
TMAC windows application "change mac address"
SMAC windows application "change mac address"

- Spoof a MAC address of Linux machine using macchanger
ifconfig eth0 down
macchanger -s eth0 (print mac address)
macchanger -a eth0 (random vendor, same kind)
macchanger -r eth0 (random mac)
ifconfig eth0 up

## Perform network sniffing using various sniffing tools

- Perform password sniffing using Wireshark
NOTE: start "Remote Packet Capture Protocol v.0"
catpure in wireshark using "Remote interfaces"

- Analyze a network using the Omnipeek Network Protocol Analyzer
require sign up

- Analyze a network using the SteelCentral Packet Analyzer
require sign up

## Detect network sniffing

- Detect ARP poisoning and promiscuous mode in a switch-based network
- wireshark "Analyze" -> Expert Information
nmap --script=sniffer-detect [Target IP Address/IP Address Range]

- Detect ARP poisoning using the Capsa Network Analyzer
require signup
habu.arp.poison 10.10.1.11 10.10.1.13