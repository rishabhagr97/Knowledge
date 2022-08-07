# Identify Hash
We can identify hash using Hash Identifier - https://gitlab.com/kalilinux/packages/hash-identifier

# Playing with john
To get list of specific hashes
```bash
john --list=formats | grep -iF "md5"
```
Common Usage
```bash
john --format=[format] --wordlist=[path to wordlist] [path to file]
```
# Cracking Windows Hashes
Dump using mimikatz and othe tools or dump NTDS.dit in windows server then crack using john.
Mode- NT

# Cracking Linux Hashes
Dump /etc/shadow and /etc/passwd files and unshadow them using following command -
```bash
unshadow [path to passwd] [path to shadow] >> output.txt
```
Then crack using john with format SHA512crypt
