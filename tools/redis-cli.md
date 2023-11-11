# `redis-cli`

Used to connect to a Redis database.

### To access a remote Redis server
redis-cli -h <hostname> -p <port> -a <password>

### Some useful commands
- `SELECT 0`: Select index database.
- `DBSIZE`: Get the size of the database.
- `KEYS *`: Show all keys.
- `GET {key}`: Show the content of a specific key.
