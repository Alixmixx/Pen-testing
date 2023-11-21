# `volatility`

The Volatility Framework is a completely open collection of tools,
implemented in Python under the GNU General Public License, for the
extraction of digital artifacts from volatile memory (RAM) samples.

## https://github.com/volatilityfoundation/volatility

## Analyze dmp file

## List Running Processes in the memory dump:
volatility -f <memory_dump_file> pslist

## Display Network Connections:
volatility -f <memory_dump_file> netscan

## Analyze Registry Hives:
volatility -f <memory_dump_file> hivelist

## Identify Loaded Kernel Modules:
volatility -f <memory_dump_file> modules

## Extracting Process Memory:
volatility -f <memory_dump_file> --profile=<profile> procdump -p <pid> -D <output_directory>

## Timeline Analysis:
volatility -f <memory_dump_file> --profile=<profile> timeline
