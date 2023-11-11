# `gobuster`

A fuzzer tool for finding domains and directories in URLs using wordlists.

### Available commands
  dir         Uses directory/file enumeration mode
  dns         Uses DNS subdomain enumeration mode
  fuzz        Uses fuzzing mode
  help        Help about any command
  s3          Uses aws bucket enumeration mode
  version     shows the current version
  vhost       Uses VHOST enumeration mode

### To find subdomains
gobuster vhost -u <hostname> -w <wordlist> --append-domain

### To find subdirectories
gobuster dir -u <hostname> -w <wordlist>

