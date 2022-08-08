# Common Commands
List IP addresses to scan. Do not scan actually.
```bash
nmap -sL -n <IP Range>.
```
To ignore Reverse DNS lookup use -n

To force reverse DNS for offline hosts also use -R

To do fast scan for first 100 default ports use -F

To do port scan in consecutive order use -r

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

TCP SYN Ping - Sends SYN, Receives SYN/RST
```bash
nmap -PS<ports or leave blank> -sn <IP>
```
TCP ACK Ping - Sends ACK, Receives RST
```bash
nmap -PA<ports or leave blank> -sn <IP>
```
UDP Ping
```bash
nmap -PU -sn <IP>
```
