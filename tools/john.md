##`john` (John the Ripper)

John the Ripper is an Open Source password security auditing and password recovery tool

### To crack a hash
echo <hash> > hash.txt
john hash.txt

### You can also use a wordlist to crack the hash
john -w=/usr/share/wordlist hash.txt

### Useful wordlists
rockyou.txt
Seclist/john-the-ripper.txt
