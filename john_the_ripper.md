# Identify Hash
We can identify hash using Hash Identifier - https://gitlab.com/kalilinux/packages/hash-identifier

# Playing with john
To get list of specific hashes
```bash
john --list=formats | grep -iF "md5"
```
Common USage
```bash
john --format=[format] --wordlist=[path to wordlist] [path to file]
```
