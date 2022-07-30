
# Important Site References

 - [Impacket](https://github.com/SecureAuthCorp/impacket)
 - [Payload All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings)

## Linux Enumeration and Exploitation

- [Basic Linux privilege escalation](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/)
- [LinEnum](https://github.com/rebootuser/LinEnum)
- [Linux Smart Enumeration](https://github.com/diego-treitos/linux-smart-enumeration/blob/master/lse.sh)
- [Linux Exploit Suggestor](https://github.com/mzet-/linux-exploit-suggester)
- [gtfobins](https://gtfobins.github.io/gtfobins/su/)

## Windows Enumeration and Exploitation

- [Fuzzy Security](https://www.fuzzysecurity.com/tutorials/16.html)
- [PowerSploit](https://github.com/PowerShellMafia/PowerSploit)
- [JAWS](https://github.com/411Hall/JAWS)


# Important Tools
## Ghidra
Tool to analyse any binary.
## GoBuster
Tool to bruteforce subdirectories for a host.

#### Basic command to enumerate directories from a wordlist -
```bash
gobuster dir -u http://<ip>:3333 -w <word list location>
```
```text
Basic Usage:
  gobuster dir [flags]

Flags:
  -u, --url string                    The target URL
  -w, --wordlist string               Path to the wordlist
  -e, --expanded                      Expanded mode, print full URLs
  -U, --username string               Username for Basic Auth
  -P, --password string               Password for Basic Auth
  -p, --proxy string                  Proxy to use for requests [http(s)://host:port]
  -c, --cookies string                Cookies to use for the requests
  -r, --follow-redirect               Follow redirects
```

## Nikto
nikto is a popular web scanning tool that allows users to find common web vulnerabilities. It is commonly used to check for common CVE's such as shellshock, and to get general information about the web server that you're enumerating.

## Hashcat
To use attack modes use -a. For dictionary 0 and for bruteforce 3
To use hash type use -m
```bash
hashcat -a {Attack Mode} -m {Hash Mode} {hash} {wordlist} 
```

## Hydra
```bash
hydra -l <username> -P <full path to pass> ftp://MACHINE_IP
hydra -l <username> -P <full path to pass> MACHINE_IP -t 4 ssh
hydra -l <username> -P <wordlist> MACHINE_IP http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V
```
For GUI, we can use xhydra or hydra-wizard

## Nmap
https://tryhackme.com/room/furthernmap

When port scanning with Nmap, there are three basic scan types. These are:
- TCP Connect Scans (-sT)
- SYN "Half-open" Scans (-sS)
- UDP Scans (-sU)

Additionally there are several less common port scan types, some of which we will also cover (albeit in less detail). These are:
- Null Scans (-sN)
- TCP FIN Scans (-sF)
- TCP Xmas Scans (-sX)

### Aggressive Scan – Scan all scripts and types
-A => This enables OS detection (-O), version scanning (-sV), script scanning (-sC) and traceroute (--traceroute)

### TCP Connect Scan
TCP Connect scan works by performing the three-way handshake with each target port in turn. In other words, Nmap tries to connect to each specified TCP port, and determines whether the service is open by the response it receives.

If Nmap sends a TCP request with the SYN flag set to a closed port, the target server will respond with a TCP packet with the RST (Reset) flag set. By this response, Nmap can establish that the port is closed.
![alt text](https://github.com/1606iamrishabhagrawal/Knowledge/blob/main/images/image9.png?raw=true)
![alt text](https://github.com/1606iamrishabhagrawal/Knowledge/blob/main/images/image10.png?raw=true)

If, however, the request is sent to an open port, the target will respond with a TCP packet with the SYN/ACK flags set. Nmap then marks this port as being open (and completes the handshake by sending back a TCP packet with ACK set). 

Many firewalls are configured to simply drop incoming packets. Nmap sends a TCP SYN request, and receives nothing back. This indicates that the port is being protected by a firewall and thus the port is considered to be filtered.

![alt text](https://github.com/1606iamrishabhagrawal/Knowledge/blob/main/images/image11.png?raw=true)

### SYN Scan
As with TCP scans, SYN scans (-sS) are used to scan the TCP port-range of a target or targets; however, the two scan types work slightly differently. SYN scans are sometimes referred to as "Half-open" scans, or "Stealth" scans.

Where TCP scans perform a full three-way handshake with the target, SYN scans sends back a RST TCP packet after receiving a SYN/ACK from the server (this prevents the server from repeatedly trying to make the request). In other words, the sequence for scanning an open port looks like this:

![alt text](https://github.com/1606iamrishabhagrawal/Knowledge/blob/main/images/image12.png?raw=true)

![alt text](https://github.com/1606iamrishabhagrawal/Knowledge/blob/main/images/image13.png?raw=true)

This has a variety of advantages for us as hackers:
- It can be used to bypass older Intrusion Detection systems as they are looking out for a full three way handshake. This is often no longer the case with modern IDS solutions; it is for this reason that SYN scans are still frequently referred to as "stealth" scans.
- SYN scans are often not logged by applications listening on open ports, as standard practice is to log a connection once it's been fully established. Again, this plays into the idea of SYN scans being stealthy.
- Without having to bother about completing (and disconnecting from) a three-way handshake for every port, SYN scans are significantly faster than a standard TCP Connect scan.

There are, however, a couple of disadvantages to SYN scans, namely:
- They require sudo permissions[1] in order to work correctly in Linux. This is because SYN scans require the ability to create raw packets (as opposed to the full TCP handshake), which is a privilege only the root user has by default.
- Unstable services are sometimes brought down by SYN scans, which could prove problematic if a client has provided a production environment for the test.

SYN scans are the default scans used by Nmap if run with sudo permissions.

### UDP Scans

Unlike TCP, UDP connections are stateless. This means that, rather than initiating a connection with a back-and-forth "handshake", UDP connections rely on sending packets to a target port and essentially hoping that they make it. This makes UDP superb for connections which rely on speed over quality (e.g. video sharing), but the lack of acknowledgement makes UDP significantly more difficult (and much slower) to scan. The switch for an Nmap UDP scan is (-sU)

When a packet is sent to an open UDP port, there should be no response. When this happens, Nmap refers to the port as being open|filtered. In other words, it suspects that the port is open, but it could be firewalled. If it gets a UDP response (which is very unusual), then the port is marked as open. More commonly there is no response, in which case the request is sent a second time as a double-check. If there is still no response then the port is marked open|filtered and Nmap moves on.

When a packet is sent to a closed UDP port, the target should respond with an ICMP (ping) packet containing a message that the port is unreachable. This clearly identifies closed ports, which Nmap marks as such and moves on.
 

Due to this difficulty in identifying whether a UDP port is actually open, UDP scans tend to be incredibly slow in comparison to the various TCP scans (in the region of 20 minutes to scan the first 1000 ports, with a good connection). For this reason it's usually good practice to run an Nmap scan with --top-ports <number> enabled. For example, scanning with  nmap -sU --top-ports 20 <target>. Will scan the top 20 most commonly used UDP ports, resulting in a much more acceptable scan time.

### Ping scan - Active Hosts Scanning
On first connection to a target network in a black box assignment, our first objective is to obtain a "map" of the network structure -- or, in other words, we want to see which IP addresses contain active hosts, and which do not.

One way to do this is by using Nmap to perform a so called "ping sweep".

To perform a ping sweep, we use the -sn switch in conjunction with IP ranges which can be specified with either a hypen (-) or CIDR notation. i.e. we could scan the 192.168.0.x network using:

```bash
nmap -sn 192.168.0.1-254
```

### NSE scripts
There are many categories available. Some useful categories include:
- safe:- Won't affect the target
- intrusive:- Not safe: likely to affect the target
- vuln:- Scan for vulnerabilities
- exploit:- Attempt to exploit a vulnerability
- auth:- Attempt to bypass authentication for running services (e.g. Log into an FTP server anonymously)
- brute:- Attempt to bruteforce credentials for running services
- discovery:- Attempt to query running services for further information about the network (e.g. query an SNMP server).
To run a specific script, we would use --script=<script-name> , e.g. --script=http-fileupload-exploiter.

Multiple scripts can be run simultaneously in this fashion by separating them by a comma. For example: --script=smb-enum-users,smb-enum-shares.

Some scripts require arguments (for example, credentials, if they're exploiting an authenticated vulnerability). These can be given with the --script-args Nmap switch. An example of this would be with the http-put script (used to upload files using the PUT method). This takes two arguments: the URL to upload the file to, and the file's location on disk.  For example:
```bash
nmap -p 80 --script http-put --script-args http-put.url='/dav/shell.php',http-put.file='./shell.php'
```
Note that the arguments are separated by commas, and connected to the corresponding script with periods (i.e.  <script-name>.<argument>).

Nmap scripts come with built-in help menus, which can be accessed using nmap --script-help <script-name>. This tends not to be as extensive as in the link given above, however, it can still be useful when working locally.

Nmap stores its scripts on Linux at /usr/share/nmap/scripts.

There are two ways to search for installed scripts. One is by using the /usr/share/nmap/scripts/script.db file.

### Windows default firewall evasion
Your typical Windows host will, with its default firewall, block all ICMP packets. This presents a problem: not only do we often use ping to manually establish the activity of a target, Nmap does the same thing by default. This means that Nmap will register a host with this firewall configuration as dead and not bother scanning it at all.

So, we need a way to get around this configuration. Fortunately Nmap provides an option for this: -Pn, which tells Nmap to not bother pinging the host before scanning it. This means that Nmap will always treat the target host(s) as being alive, effectively bypassing the ICMP block; however, it comes at the price of potentially taking a very long time to complete the scan (if the host really is dead then Nmap will still be checking and double checking every specified port).

# Information Gathering Tools
- Sublist3r
- hunter.io
- builtwith.com
- wappalyzer
- dnsdumpster (site)
- nslookup and dig

# Exploit Databases and Search Tools
- Exploit Db
- Nvd nist

# Vulnerability Scanning Tools
- Nikto
- Owasp-zap

