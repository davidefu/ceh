# Hacking webserver

## Footprint the web server

- Information gathering using Ghost Eye
python3 ghost_eye.py
3 - Whois lookup
2 - DNS lookup
6 - Clickjacking Test

- Perform web server reconnaissance using Skipfish
`skipfish -o /home/attacker/test -S /usr/share/skipfish/dictionaries/complete.wl http://[IPAddress of Windows Server 2022]:8080`

- Footprint a web server using the httprecon Tool  
    windows software

- Footprint a web server using ID Serve  
    windows software

- Footprint a web server using Netcat and Telnet
nc -vv www.moviescope.com 80
    GET / HTTP/1.0
telnet www.moviescope.com 80
    GET / HTTP/1.0

- Enumerate web server information using Nmap Scripting Engine (NSE)

```bash
nmap -sV --script=http-enum [target website]
nmap --script hostmap-bfk -script-args hostmap-bfk.prefix=hostmap-www.goodshopping.com (discover the hostnames that resolve the targeted domain)
nmap --script http-trace -dwww.goodshopping.com
nmap-p80 --script http-waf-detect www.goodshopping.com
```

- Uniscan web server fingerprinting in Parrot Security

```bash
uniscan -u http://10.10.1.22:8080/CEH -q (directory scan)
uniscan -u http://10.10.1.22:8080/CEH -we (robots.txt and sitemap.xml)
uniscan -u http://10.10.1.22:8080/CEH -d (dynamic testing)
```

## Perform a web server attack

- Crack FTP credentials using a Dictionary Attack
`hydra -L /home/attacker/Desktop/Wordlists/Usernames.txt -P/home/attacker/Desktop/Wordlists/Passwords.txt ftp://[IP Address of Windows 11]`
