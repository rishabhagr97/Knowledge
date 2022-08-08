# Common Commands
List IP addresses to scan. Do not scan actually.
```bash
nmap -sL -n <IP Range>.
```
# Host Discovery
There are 3 methods to do host discovery
- ARP scan: This scan uses ARP requests to discover live hosts
- ICMP scan: This scan uses ICMP requests to identify live hosts
- TCP/UDP ping scan: This scan sends packets to TCP ports and UDP ports to determine live hosts.


## Host discovertry using ARP
ARP Scan without Port scanning
```bash
nmap -PR -sn <IP Range>.
```
Another better tool for arp scan can be found here http://www.royhills.co.uk/wiki/index.php/Main_Page.

We can use following command to scan whole lcoal network.
```bash
arp-scan -l
```

## Host discovertry using ICMP
Sending ICMP Echo Requests
```bash
nmap -PE -sn <IP>
```
Sending ICMP Timestamp request as ICMP echo is blocked in many devices.
```bash
nmap -PP -sn <IP>
```
Sending ICMP Address Mask request.
```bash
nmap -PM -sn <IP>
```

## Host discovertry using TCP/UDP


