# Scanning

## Perform host discovery

- Perform host discovery using **Nmap**  
    ARP Ping: `nmap -sn -PR [Target IP Address]`  
    UDP Ping: `nmap -sn -PU [Target IP Address]`  
    ICMP ECHO Ping: `nmap -sn -PE [Target IP Address]`  
    ICMP timestamp ping: `nmap -sn -PP [Target IP Address]`  
    ICMP Address mask ping Ping: `nmap -sn -PM [Target IP Address]`  
    TCP SYN Ping: `nmap -sn -PS [Target IP Address]`  
    TCP ACK Ping: `nmap -sn -PA [Target IP Address]`  
    IP Protocol Ping: `nmap -sn -PO [Target IP Address]`  

- Perform host discovery using **Angry IP Scanner**

## Perform port and service discovery

- Perform port and service discovery using **MegaPing**  
    windows software

- Perform port and service discovery using **NetScanTools Pro**  
    Manual tools (all) -> Ping scanner  
                       -> Port scanner

- Perform port scanning using **sx** tool  
    `sx arp [Target subnet] --json`  
    `sx udp [Target subnet] -p [port]`

- Explore various network scanning techniques using **Nmap**  
    `-sT` TCP full open  
    `-sS` stealth scan  
    `-sX` Xmas scan (If the target has openedthe port, then you will receive no response from the target system. If the target has closed the port, then you willreceive a target system reply with an RST.)  
    `-sM` Maimon scan (a FIN/ACK probe is sent to the target; if there is no response, then the port isOpen|Filtered, but if the RST packet is sent as a response, then the port is closed)  
    `-sA` ACK scan (no response impliesthat the port is filtered (stateful firewall is present), and an RST response means that the port is not filtered)  
    `-sU` UDP scan (no response means that the port is open. If the port is closed, an ICMP port unreachable message is received.)  
    `-sN` Null scan  
    `-sI` IDLE-IPID spoofed source address  
    `-sY` SCTP INIT Scan (An INIT chunk is sent to the target host; an INIT+ACK chunk response implies that the port is open, andan ABORT Chunk response means that the port is closed)  
    `-sZ` SCTP COOKIE ECHO Scan (A COOKIE ECHO chunk is sent to the target host; no response implies that the port is openand ABORT Chunk response means that the port is closed)  

    `-A` advanced aggressive includes:  
        `-sV` detects service versions  
        `-O` OS detection  
        `--traceroute`  

- Explore various network scanning techniques using **Hping3**  
  - `hping3 -A [Target IP Address] -p 80 -c 5`  
        -A ACK flag  
        -p port  
        -c packet count  
  - `hping3 -F -P -U [Target IP Address] -p 80 -c 5`  
        -F FIN flag  
        -P PUSH flag  
        -U URG flag  
        -S SYN flag  
  - `hping3 --scan 0-100 -S [target ip address]`  
  - `hping3 -1 [Target IP Address] -p 80 -c 5`  
        -1 ICMP ping scan  
  - `hping3 -1 [Target Subnet] --rand-dest -I eth0`  
    Entire subnet scan for live host  
    sample target subnet: 10.0.1.x
  - `hping3 -2 [Target IP Address] -p 80 -c 5`  
    UDP scan

## Perform OS discovery

- Identify the target system’s OS with Time-to-Live (TTL) and TCP window sizes using **Wireshark**
OS | TTL | Window
Linux | 64 | 5840
FreeBSD | 64 | 65535
OpenBSD | 255 | 16384
Windows | 128 | 65535 to 1 GB
Cisco | 255 | 4128
Solaris | 255 | 8760
AIX | 255 | 16384

- Perform OS discovery using **Nmap Script Engine (NSE)**  
    `nmap --script smb-os-discovery.nse [Target IP Address] -A -O -sV`
- Perform OS discovery using **Unicornscan**  
    `unicornscan [Target IP Address] -Iv`

## Scan beyond IDS and Firewall

- Scan beyond IDS/firewall using various **evasion techniques**  
  - `nmap -f [Target IP Address]`  
    -f split packet
  - `nmap -g 80 [Target IP Address]`
    -g or --source-port to modify the source port of the scan
  - `nmap -mtu 8 [Target IP Address]`
  - `nmap -D RND:10 [Target IP Address]`  
    decoy scan, randomly creating 10 IP and randomly positions the real IP address between the decoy IP
  - `nmap -sT -Pn --spoof-mac 0 [Target IP Address]`  
    --spoof-mac randoming MAC address  
    -Pn skip host discovery

- Create custom packets using **Colasoft Packet Builder** to scan beyond the IDS/firewall  
    ARP Packet template, set Delta Time as 0.1  
    Send All Packets window, check the Burst Mode

- Create custom UDP and TCP packets using **Hping3** to scan beyond the IDS/firewall  
  - `hping3 [Target IP Address] --udp --rand-source --data 500`
  - `hping3 -S [Target IP Address] -p 80 -c 5` -S TCP SYN
  - `hping3 [Target IP Address] --flood` TCP flooding

## Perform network scanning using various scanning tools

- Scan a target network using **Metasploit**  
    `nmap -Pn -sS -A -oX Test 10.10.1.0/24`  
    `db_import Test`  
    `hosts`  
    `db_services`  
    `use auxiliary/scanner/portscan/syn` SYN scan  
    `use auxiliary/scanner/portscan/tcp` TCP scan  
    `use auxiliary/scanner/smb/smb_version`
