# Common Commands
List IP addresses to scan. Do not scan actually.
```bash
nmap -sL -n <IP Range>.
```
OS Detection = -O

Traceroute = --traceroute

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

# Spoofing
## Spoof IP Address
To spoof attacker's IP address, use following command -
```bash
nmap -e NET_INTERFACE -Pn -S SPOOFED_IP ATTACK_IP
```
Nmap will craft all the packets using the provided source IP address SPOOFED_IP. The target machine will respond to the incoming packets sending the replies to the destination IP address SPOOFED_IP. For this scan to work and give accurate results, the attacker needs to monitor the network traffic to analyze the replies.
Ping scan will not work so we disabled it. And, NET_INTERFACE is the interface that is used for spoofing IP.
## Spoof MAC Address
When you are on the same subnet as the target machine, you would be able to spoof your MAC address as well. You can specify the source MAC address using --spoof-mac SPOOFED_MAC. This address spoofing is only possible if the attacker and the target machine are on the same Ethernet (802.3) network or same WiFi (802.11).
## Decoys
You can launch a decoy scan by specifying a specific or random IP address after -D. For example, 
```bash
nmap -D 10.10.0.1,10.10.0.2,ME 10.10.167.3
```
will make the scan of 10.10.167.3 appear as coming from the IP addresses 10.10.0.1, 10.10.0.2, and then ME to indicate that your IP address should appear in the third order. Another example command would be
```bash
nmap -D 10.10.0.1,10.10.0.2,RND,RND,ME 10.10.167.3
```
where the third and fourth source IP addresses are assigned randomly, while the fifth source is going to be the attacker’s IP address. In other words, each time you execute the latter command, you would expect two new random IP addresses to be the third and fourth decoy sources.

# Fragmented Packets
Nmap provides the option -f to fragment packets. Once chosen, the IP data will be divided into 8 bytes or less. Adding another -f (-f -f or -ff) will split the data into 16 byte-fragments instead of 8. You can change the default value by using the --mtu; however, you should always choose a multiple of 8.

On the other hand, if you prefer to increase the size of your packets to make them look innocuous, you can use the option --data-length NUM, where num specifies the number of bytes you want to append to your packets.

Spoofing the source IP address can be a great approach to scanning stealthily. However, spoofing will only work in specific network setups. It requires you to be in a position where you can monitor the traffic. Considering these limitations, spoofing your IP address can have little use; however, we can give it an upgrade with the idle scan.

# Idle/Zombie Scan
The idle scan, or zombie scan, requires an idle system connected to the network that you can communicate with. Practically, Nmap will make each probe appear as if coming from the idle (zombie) host, then it will check for indicators whether the idle (zombie) host received any response to the spoofed probe. This is accomplished by checking the IP identification (IP ID) value in the IP header. You can run an idle scan using nmap -sI ZOMBIE_IP 10.10.167.3, where ZOMBIE_IP is the IP address of the idle host (zombie).

# Resoning
For more detailing we can use --reason that will specify why the post is open. And, for further detailing we can use -vv or for more -d or -dd.

# Service Detection
Adding -sV to your Nmap command will collect and determine service and version information for the open ports. You can control the intensity with --version-intensity LEVEL where the level ranges between 0, the lightest, and 9, the most complete. -sV --version-light has an intensity of 2, while -sV --version-all has an intensity of 9.

It is important to note that using -sV will force Nmap to proceed with the TCP 3-way handshake and establish the connection. The connection establishment is necessary because Nmap cannot discover the version without establishing a connection fully and communicating with the listening service. In other words, stealth SYN scan -sS is not possible when -sV option is chosen.

# NSE Scripts
You can choose to run the scripts in the default category using --script=default or simply adding -sC. In addition to default, 

auth            Authentication related scripts
broadcast       Discover hosts by sending broadcast messages
brute           Performs brute-force password auditing against logins
default         Default scripts, same as -sC
discovery       Retrieve accessible information, such as database tables and DNS names
dos             Detects servers vulnerable to Denial of Service (DoS)
exploit         Attempts to exploit various vulnerable services
external        Checks using a third-party service, such as Geoplugin and Virustotal
fuzzer          Launch fuzzing attacks
intrusive       Intrusive scripts such as brute-force attacks and exploitation
malware         Scans for backdoors
safe            Safe scripts that won’t crash the target
version         Retrieve service versions
vuln            Checks for vulnerabilities or exploit vulnerable services


You can also specify the script by name using --script "SCRIPT-NAME" or a pattern such as --script "ftp*", which would include ftp-brute. If you are unsure what a script does, you can open the script file with a text reader.
