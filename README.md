
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

