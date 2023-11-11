# `nmap` (Network Mapper)

 - Network Scanner

### To probe open ports and check their service/version
nmap -sV <hostname>

### To check all ports
nmap -p- <hostname>

### Specific port
nmap -p433 <hostname>

### To enable script scanning
nmap -sC <hostname>

### To perform OS detection
nmap -O <hostname>


### SCAN TECHNIQUES
  -sS/sT/sA/sW/sM: TCP SYN/Connect()/ACK/Window/Maimon scans
  -sU: UDP Scan
  -sN/sF/sX: TCP Null, FIN, and Xmas scans
  --scanflags <flags>: Customize TCP scan flags
  -sI <zombie host[:probeport]>: Idle scan
  -sY/sZ: SCTP INIT/COOKIE-ECHO scans
  -sO: IP protocol scan
  -b <FTP relay host>: FTP bounce scan
