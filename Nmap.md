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


# Advance Port Scanning
##NUL Scan
The null scan does not set any flag; all six flag bits are set to zero. A TCP packet with no flags set will not trigger any response when it reaches an open port. Therefore, from Nmap’s perspective, a lack of reply in a null scan indicates that either the port is open or a firewall is blocking the packet.
```bash
nmap -sN <IP>
````
##FIN Scan
The FIN scan sends a TCP packet with the FIN flag set. No response will be sent if the TCP port is open.
However, the target system should respond with an RST if the port is closed. Consequently, we will be able to know which ports are closed and use this knowledge to infer the ports that are open or filtered. It's worth noting some firewalls will 'silently' drop the traffic without sending an RST.
```bash
nmap -sF <IP>
````
##Xmas Scan
The Xmas scan gets its name after Christmas tree lights. An Xmas scan sets the FIN, PSH, and URG flags simultaneously.
Like the Null scan and FIN scan, if an RST packet is received, it means that the port is closed. Otherwise, it will be reported as open|filtered.
```bash
nmap -sX <IP>
````
##Maimon Scan
In this scan, the FIN and ACK bits are set. The target should send an RST packet as a response. However, certain BSD-derived systems drop the packet if it is an open port exposing the open ports. This scan won’t work on most targets encountered in modern networks.
Most target systems respond with an RST packet regardless of whether the TCP port is open. In such a case, we won’t be able to discover the open ports.
```bash
nmap -sM <IP>
````
##ACK Scan
an ACK scan will send a TCP packet with the ACK flag set. The target would respond to the ACK with RST regardless of the state of the port. This behaviour happens because a TCP packet with the ACK flag set should be sent only in response to a received TCP packet to acknowledge the receipt of some data, unlike our case. Hence, this scan won’t tell us whether the target port is open in a simple setup.

This kind of scan would be helpful if there is a firewall in front of the target. Consequently, based on which ACK packets resulted in responses, you will learn which ports were not blocked by the firewall. In other words, this type of scan is more suitable to discover firewall rule sets and configuration.
```bash
nmap -sA <IP>
````
##Window Scan
The TCP window scan is almost the same as the ACK scan; however, it examines the TCP Window field of the RST packets returned.

However, as you would expect, if we repeat our TCP window scan against a server behind a firewall, we expect to get more satisfying results. In the console output shown below, the TCP window scan pointed that three ports are detected as closed. (This is in contrast with the ACK scan that labelled the same three ports as unfiltered.) Although we know that these three ports are not closed, we realize they responded differently, indicating that the firewall does not block them.
##Custom Scan
If you want to experiment with a new TCP flag combination beyond the built-in TCP scan types, you can do so using --scanflags. For instance, if you want to set SYN, RST, and FIN simultaneously, you can do so using --scanflags RSTSYNFIN. As shown in the figure below, if you develop your custom scan, you need to know how the different ports will behave to interpret the results in different scenarios correctly.
