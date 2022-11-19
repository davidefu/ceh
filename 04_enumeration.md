# Enumeration

## Perform NetBIOS enumeration

- Perform NetBIOS enumeration using Windows command-line utilities **nbtstat** and **net use**
  - `nbtstat -A [IP address of the remote machine]`  
    -a netbios name table
  - `nbtstat -c`  
    -c contents of the netbios name cache
  - `net use`

- Perform NetBIOS enumeration using **NetBIOS Enumerator**  
    (windows software with ui)

- Perform NetBIOS enumeration using **nmap NSE Script**  
  - `nmap -sV -v --script nbstat.nse [Target IP Address]`
  - `nmap -sU -p 137 --script nbstat.nse [Target IP Address]`

## Perform SNMP enumeration

- Perform SNMP enumeration using **snmp-check**
  - `nmap -sU -p 161 [Target IP address]`
  - `snmp-check [Target IP Address]`

- Perform SNMP enumeration using **SoftPerfect Network Scanner**  
    (windows software with ui)

- Perform SNMP enumeration using **SnmpWalk**  
  - `snmpwalk -v1 -c public [target IP]`
    -v (version: 1,2c,3 )
    -c community string

- Perform SNMP enumeration using **Nmap**  
  - `nmap -sU -p 161 --script=snmp-sysdescr [target IP Address]`
  - `nmap -sU -p 161 --script=snmp-processes [target IP Address]`
  - `nmap -sU -p 161 --script=snmp-win32-software [target IP Address]`
  - `nmap -sU -p 161 --script=snmp-interfaces [target IP Address]`

## Perform LDAP enumeration

- Perform LDAP enumeration using **Active Directory Explorer (AD Explorer)**

- Perform LDAP enumeration using Python and **Nmap**  
    `nmap -sU -p 389 [Target IP address]`
    `nmap -p 389 --script ldap-brute --script-args ldap.base='"cn=users,dc=CEH,dc=com"' [Target IP Address]`

```python
import ldap3
server=ldap3.Server(’[Target IP Address]’, get_info=ldap3.ALL,port=[Target Port])
connection=ldap3.Connection(server)
connection.bind()
server.info
connection.search(search_base='DC=CEH,DC=com',search_filter='(&(objectclass=*))',search_scope='SUBTREE', attributes='*')
connection.entries
connection.search(search_base='DC=CEH,DC=com',search_filter='(&(objectclass=person))',search_scope='SUBTREE', attributes='userpassword')
connection.entries
```

- Perform LDAP enumeration using **ldapsearch**  

  - `ldapsearch -h [Target IP Address] -x -s base namingcontexts`  
    -x simple authetication  
    -s scope  

  - `ldapsearch -h [Target IP Address] -x -b “DC=CEH,DC=com”`  
    -b base DN for search

## Perform NFS enumeration

- Perform NFS enumeration using **RPCScan and SuperEnum**  
    `nmap -p 2049 [Target IP Address]`  

    `./superenum`  
    `python3 rpc-scan.py [Target IP address] --rpc`

## Perform DNS enumeration

- Perform DNS enumeration using zone transfer  
    `dig ns [Target Domain]`  
    `@[[NameServer]] [[Target Domain]] axfr`  

```bash
nslookup
set querytype=soa -- to retrieve dns info
ls -d [Name Server] -- zone transfer
```

- Perform DNS enumeration using DNSSEC zone walking  
    `./dnsrecon.py -d [Target domain] -z`

- Perform DNS enumeration using **Nmap**  
    `nmap --script=broadcast-dns-service-discovery [Target Domain]` -- rDNS record  
    `dig -x 193.33.178.182 +noall +answer` also for RDNS  (the result is reversed)  
    `nmap -T4 -p 53 --script dns-brute [Target Domain]`  
    `nmap --script dns-srv-enum --script-args "dns-srv-enum.domain='[Target Domain]'”`  

## Perform SMTP Enumeration

- Perform SMTP enumeration using **Nmap**  
    `nmap -p 25 --script=smtp-enum-users [Target IP Address]`  
    `nmap -p 25 --script=smtp-open-relay [Target IP Address]`  
    `nmap -p 25 --script=smtp-commands [Target IP Address]`

## Perform RPC, SMB, and FTP enumeration

- Perform SMB and RPC enumeration using **NetScanTools Pro**  
    (windows application with ui)  
    Smb scanner  
    Manual tools --> *nix RPC Info  

- Perform RPC, SMB, and FTP enumeration using **Nmap**  
  - `nmap -p 21 [Target IP Address]`
  - `nmap -T4 -A [Target IP Address]`
  - `nmap -p445 --script smb-protocols <target>`

## Perform enumeration using various enumeration tools

- Enumerate information using **Global Network Inventory**
    (windows software with UI)  
    New audit wizard  

- Enumerate network resources using **Advanced IP Scanner**

- Enumerate information from Windows and Samba hosts using **Enum4linux**  
    `enum4linux -u administrator -p 'Pa$$w0rd' [-n] [Target IP Address]`  
    -n must be changed with a options  
    -U userlist  
    -o OS information  
    -P policy information  
    -G group and member list  
    -S sharelist  
