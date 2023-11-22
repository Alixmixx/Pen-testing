# `Rsync`

Rsync is a versatile and powerful command-line utility used for file synchronization and transfer. It efficiently transfers only the differences between source and destination files, reducing the amount of data transmitted over a network.
Basic Syntax. Port 873

### Local Copy:
rsync -av /path/to/source /path/to/destination

### Remote Copy over SSH:
rsync -av -e ssh user@remote:/path/to/source /path/to/destination


###  Dry Run (Preview):

    rsync -av --dry-run /path/to/source /path/to/destination
    The --dry-run option shows what rsync would do without actually making any changes.

a reliable and efficient tool for various file synchronization tasks, offering flexibility and customization through its numerous options.