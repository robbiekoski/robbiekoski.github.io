---
layout: default
title: Tool Notes
nav_order: 5
---

# Tool Notes
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Nmap
Used for information gathering, port scanning, OS detection, etc.
  - v : enables verbose output mode, always use!
  - sV : probes open ports to determine service/version info
  - sC : default script scan
  - oN : save output to a file
  - Pn : treats all hosts as online, skips host discovery, use with sudo
  - O: enables OS detection
  - A : enable os detection, version detection, script scanning, and traceroute
  - p : enables port range scanning

```
EXAMPLES: nmap -v -sV -sC -oN nmap.log 10.10.2.5
          nmap -v -p1-300 10.10.2.5
```

## Netdiscover
Used to scan for hosts on a network
  - r : scan a given range of addresses

```
EXAMPLE: netdiscover 10.10.2.0/24
```

## Gobuster
Used for enumerating web directories
  - dir : used for directory/file enumeration mode
  - e : print the full URLs in console output
  - u : specify the target URL
  - w : specify the wordlist

```
EXAMPLE: gobuster dir -e -u http://10.10.2.5/ -w /opt/rockyou.txt
```

## Netcat
Used to set up a port listener for gaining reverse shells
  - l : enables listen mode
  - v : enables verbose
  - n : does not resolve hostnames via DNS
  - p : specifies a source port to use

```
EXAMPLE: nc -lvnp 1234
```

## Hydra
Brute force authentication of many protocols
  - l : specify a static username
  - L : specify a username wordlist
  - p : specify a static password
  - P : specify a password wordlist (rockyou.txt)
  - v : enables verbose mode
  - V : show login:pass for each attempt

```
EXAMPLES: hydra -l jan -P /opt/rockyou.txt ssh://10.10.2.5 -vV
          hydra -L /opt/userlist.txt -p password123 ssh://10.10.2.5 -vV
          hydra -l charlie -P /opt/rockyou.txt 10.10.2.5 http-post-form "/index.php:uname=charlie&password=^PASS^&submit=Log+In:Incorrect Credentials" -vV 
```

## John the Ripper 
Used for password cracking
  - --wordlist= : specify a wordlist (rockyou.txt)

```
EXAMPLE: john password.txt --wordlist=/opt/rockyou.txt
```

## Ssh2john
Used to convert files to a readable John the Ripper format

```
EXAMPLE: ssh2john id_rsa > forjohn.txt
```

## Steghide
Used to embed data within data
  **embed**
    - cf : specify the cover file (file used to embed data)
    - ef : specify the embedded file (file that will be embedded)
  **extract**
    - sf : specify a file to extract data from

```
EXAMPLE: steghide embed -cf coverfile.jpg ef embedfile.txt
         steghide extract -sf stegfile.jpeg
```

## Stegseek
Used to quickly bruteforce steghide passphrase
  - --crack : crack a stego file using a wordlist
  - --seed : crack a stego file by attempting all embedding patterns

```
EXAMPLE: stegseek --crack stegofile.jpeg /opt/rockyou.txt
         stegseek --seed stegofile.jpeg
```

## Hashcat
Used to crack hashes
  - m : select the mode (see hashcat websites)
  - a 0 : designates a dictionary attack
  - o : specify an output file name

```
EXAMPLE: hashcat -m 1400 -o cracked.txt sha256.txt /opt/rockyou.txt
```

## Searchsploit
Used to search for exploits

```
EXAMPLE: searchsploit SweetRice
```

## Unshadow
Used to format /etc/passwd and /etc/shadow into john-readable file

```
EXAMPLE: unshadow passwd.txt shadow.txt > unshadow.txt
```

## wpscan
Used to brute force into a WordPress website
  - --url : specify the URL of the login page with .php extension
  - U : specify user text file
  - P : specify wordlist location

```
EXAMPLE: wpscan --url http://10.10.2.5/wp-login.php -U user.txt -P /opt/rockyou.txt
```
