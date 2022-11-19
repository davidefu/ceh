# Footprinting

## Perform footprinting through search engines

- Gather information using advanced Google hacking techniques
intitle:
site:
filetype:
cache:
allinurl:
inurl:
allintitle:
inanchor:
allinanchor:
link:
related:
info:
location:

- Gather information from video search engines
<https://mattw.io/youtube-metadata/>

Video analysis tools:
EZGif <https://ezgif.com>
VideoReverser.com <https://www.videoreverser.com>

Reverse image search tools:
TinEye Reverse Image Search <https://tineye.com>
Yahoo Image Search <https://images.search.yahoo.com>

- Gather information from FTP search engines
NAPALM FTP Indexer <https://www.searchftps.net/>
FreewareWeb FTP File Search <https://www.freewareweb.com>

- Gather information from IoT search engines
Shodan <https://www.shodan.io/>
Censys <https://censys.io>

## Perform footprinting through web services

- Find the company’s domains and sub-domains using Netcraft
Netcraft <https://www.netcraft.com> --> Site Report
Sublist3r
Pentest-Tools Find Subdomains

- Gather personal information using PeekYou online people search service
Peekyou <https://www.peekyou.com>
Spokeo <https://www.spokeo.com>
pipl <https://pipl.com>
Intelius <https://www.intelius.com>
BeenVerified <https://www.beenverified.com>

- Gather an email list using theHarvester
<https://github.com/laramies/theHarvester>
theHarvester -d microsoft.com -l 200 -b baidu

- Gather information using deep and dark web searching

- Determine target OS through passive footprinting
Censys <https://search.censys.io/?q=>

## Perform footprinting through social networking sites

- Gather employees’ information from LinkedIn using theHarvester
theHarvester -d eccouncil -l 200 -b linkedin

- Gather personal information from various social networking sites using Sherlock
<https://github.com/sherlock-project/sherlock>
python3 sherlock.py

- Gather information using Followerwonk
Followerwonk <https://followerwonk.com/analyze> analyze twitter
Hootsuite <https://www.hootsuite.com>
Meltwater <https://www.meltwater.com>

## Perform website footprinting

- Gather information about a target website using ping command line utility
`ping www.certifiedhacker.com -f -l 1500`
-f not fragmenting
-l buffer size

`ping www.certifiedhacker.com -i 3 -n 1`
-i time to live
-n number of echo

- Gather information about a target website using Photon
<https://github.com/s0md3v/Photon>
`python3 photon.py -u http://www.certifiedhacker.com`
`python3 photon.py -u http://www.certifiedhacker.com -l 3 -t 200 --wayback`
-l crawl level
-t threads
--wayback use archive.org

- Gather information about a target website using Central Ops
free online network scanner that investigates domains and IP addresses, DNS records, traceroute,nslookup, whois searches
<https://centralops.net>
Website Informer <https://website.informer.com>
Burp Suite <https://portswigger.net>
Zaproxy <https://www.zaproxy.org>

- Extract a company’s data using Web Data Extractor

- Mirror a target website using HTTrack Web Site Copier

- Gather information about a target website using GRecon
`python3 grecon.py`

- Gather a wordlist from the target website using CeWL
`cewl -d 2 -m 5 www.certifiedhacker.com`
-d depth
-m minimum password length
-w to output to file

## Perform email footprinting

- Gather information about a target by tracing emails using eMailTrackerPro

## Perform Whois footprinting

- Perform Whois lookup
Domain tools <http://whois.domaintools.com>
SmartWhois <https://www.tamos.com>
Batch IP Converter <http://www.sabsoft.com>

## Perform DNS footprinting

- Gather DNS information using nslookup command line utility and online tool
```bash
nslookup
set type=a (ns, aaaa, mx, cname)
```

Kloth <http://www.kloth.net/services/nslookup.php>
DNSdumpster <https://dnsdumpster.com>
DNS Records <https://network-tools.com>

- Perform reverse DNS lookup using reverse IP domain check and DNSRecon
<https://www.yougetsignal.com> --> Reverse IP Domain check
Recon
`dnsrecon.py -r 162.241.216.0-162.241.216.255`

- Gather information of subdomain and DNS records using SecurityTrails
<https://securitytrails.com/> require signup

## Perform network footprinting

- Locate the network range
<https://www.arin.net/about/welcome/region>

- Perform network tracerouting in Windows and Linux Machines

```bash
tracert -h 5 www.certifiedhacker.com (-h max hops)
```

VisualRoute <http://www.visualroute.com>
Traceroute NG <https://www.solarwinds.com>

## Perform footprinting using various footprinting tools

- Footprinting a target using Recon-ng

```bash
recon-ng
marketplace install all
workspaces create name
workspaces list
db insert domains (insert a domain in list)
modules load brute (to search)
modules load recon/domains-hosts/brute_hosts
run
back
modules load recon/domains-hosts/bing_domain_web
run
modules load recon/hosts-hosts/reverse_resolve
show hosts
modules load reporting/html
options set ...
run

modules load recon/domains-contacts/whois_pocs
modules load recon/profiles-profiles/profiler
modules load recon/domains-hosts/hackertarget (to extract a list of subdomains and IP addresses associated with the target URL)
```

- Footprinting a target using Maltego
require account

- Footprinting a target using OSRFramework
`domainfy -n [Domain Name] -t all`
`searchfy -q "target user name or profile name"`
usufy (Gathers registered accounts with given usernames)
mailfy (Gathers information about email accounts)
phonefy (Checks for the existence of a given series of phones)
entify (Extracts entities using regular expressions from provided URLs)

- Footprinting a target using FOCA
FOCA (Fingerprinting Organizations with Collected Archives) is a tool that reveals metadata and hidden information in scanneddocuments. These documents are searched for using three search engines: Google, Bing, and DuckDuckGo

- Footprinting a target using BillCipher
Using this tool, you can gather information such as DNSLookup, Whois lookup, GeoIP Lookup, Subnet Lookup, Port Scanner, Page Links, Zone Transfer, HTTP Header
<https://github.com/bahatiphill/BillCipher>
`python3 billcipher.py`

- Footprinting a target using OSINT Framework
<https://osintframework.com/>
