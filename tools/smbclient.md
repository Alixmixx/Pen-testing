# `smbclient`

Used to connect to Windows environments over SMB/CIFS.

### To list all available shares
smbclient -L <hostname>

### To connect to a specific public share
smbclient <hostname>/share

### Connect to SMB share
smbclient //<server>/<share> -U <username>
