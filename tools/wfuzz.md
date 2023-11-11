#### `wfuzz`

wfuzz is a web application security testing tool used for identifying vulnerabilities related to input validation and session management

# Example with wordlist for file paths and parameters
wfuzz -c -z file,/usr/share/wfuzz/wordlist/injection/SQL.txt -d “username=1&password=FUZZ” --hc 404 http://10.10.11.224:55555/FUZZ


# Basic Fuzzing
wfuzz -c -z file,/path/to/payloads.txt <hostname>/FUZZ
Fuzz the URL <hostname>/FUZZ by replacing FUZZ with values from the specified payloads file.

# Parameter Brute-Forcing
wfuzz -c --hc 404 -z file,/path/to/payloads.txt --hh 20 <hostname>/FUZZ?param=FUZZ2
Brute-force the parameter param in the URL <hostname>/FUZZ?param=FUZZ2 with payloads from the file. The --hc 404 option excludes HTTP 404 responses, and --hh 20 excludes responses with a header size less than 20.

# Multithreading
wfuzz -c -z file,/path/to/payloads.txt --hs 200 -t 10 <hostname>/FUZZ
Fuzz the URL with payloads from the file using 10 threads (-t 10). Exclude responses with a status code of 200 (--hs 200).

# Custom Payloads
wfuzz -c -z list,admin,root,user,backup <hostname>/FUZZ
Fuzz the URL with a custom list of payloads (admin, root, user, backup).

# Response Analysis
wfuzz -c --hl 200 <hostname>/FUZZ
Analyze responses and highlight variations in responses with a header length greater than 200 characters (--hl 200).

# Cookie Handling
wfuzz -c --hc 200 --cookie "session=FUZZ" <hostname>
Send a request with a cookie (session=FUZZ). Exclude responses with a status code of 200 (--hc 200).

# Pattern Matching
wfuzz -c --hl 50 --ps "Invalid input" <hostname>/FUZZ
Highlight responses with a header length greater than 50 characters (--hl 50) containing the pattern "Invalid input" (--ps "Invalid input").
