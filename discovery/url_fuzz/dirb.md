# `dirb`

dirb is an open-source web content scanner used in penetration testing and ethical hacking. It performs directory brute-forcing on web servers by systematically testing common directory and file names. With support for HTTP and HTTPS, recursive scanning, and custom wordlists, it helps identify hidden paths and potential security vulnerabilities on web applications. Always use such tools responsibly and with proper authorization.

### Search with a wordlist
dirb <hostname> /usr/share/wordlist

### Specify Extensions to Test
dirb -e php,html <hostname>

### Case insensitive search
dirb -i
