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

# Single Crack Mode
We sometime know the hint like name that we can use in john and john will make its own wordlist to crack password with various combination using word mangling.
To use this first add name as prefix in hash <name>:<hash>
Then crack using this command
```bash
john --single --format=[format] [path to file]
```
