# `Hydra`

Hydra is a powerful and versatile Open Source tool designed for password cracking through brute-force and dictionary attacks. Its primary purpose is to assess and reinforce the security of networked services by identifying weak or compromised credentials.
Features:

## Protocol Support:
Hydra boasts an extensive range of supported protocols, including but not limited to SSH, HTTP, FTP, Telnet, and many more.

## Parallel Attack:
Leveraging parallelized attacks, Hydra can significantly enhance the speed of its brute-force attempts, making it a formidable tool for efficiently testing password vulnerabilities.

## Flexible Authentication:
With the ability to handle a variety of authentication methods, Hydra can adapt to different login mechanisms, providing a comprehensive assessment of password security.

### Brute Force Attack:
hydra -l <username> -P <password-list> <target-service>


### Dictionary Attack:
hydra -L <username-list> -P <password-list> <target-service>

### HTTP Form-based Attack:

hydra -l <username> -P <password-list> <target-URL> http-post-form "<login-form-details>"

### Checking for Incorrect Login Attempt Responses:
hydra -l <username> -P <password-list> <target-service> -F

The -F option instructs Hydra to stop the brute-force attack as soon as it detects a valid login, helping to minimize the risk of account lockouts and increase efficiency.

### HTTP GET Request with Custom Headers:
hydra -L <username-list> -P <password-list> <target-URL> http-get -H "Custom-Header: Value"

In scenarios where custom headers are required for authentication, Hydra allows users to include these headers in their HTTP requests.

### Specifying a Delay Between Login Attempts:
hydra -l <username> -P <password-list> <target-service> -t 4

The -t option introduces a delay between login attempts, preventing rapid-fire attacks and reducing the likelihood of triggering account lockouts.

### Brute Forcing with Specific Character Sets:

hydra -l <username> -P <password-list> <target-service> -e nsr

The -e option allows users to specify character sets for the brute-force attack. In this example, it includes lowercase letters (n), special characters (s), and digits (r).

### Service-Specific Modules - SSH Example:
hydra -l <username> -P <password-list> <target-IP> ssh

Hydra supports service-specific modules. In this case, the ssh module is specified for targeting SSH services.

### Customizing Login Attempts for HTTP Form-based Attacks:
hydra -l <username> -P <password-list> <target-URL> http-post-form "/login.php:username=^USER^&password=^PASS^&submit=Login:Invalid Password"

### Wordlists:
rockyou.txt
Seclist/john-the-ripper.txt

