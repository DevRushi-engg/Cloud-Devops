# awk — Work With Fields and Columns

## What it does
Splits each line into fields and lets you print, filter, or
calculate with them. More powerful than cut for complex column work.

## Syntax
```bash
awk '{print $1}' file.txt          # print first column
awk '{print $1, $3}' data.txt      # print columns 1 and 3
awk -F',' '{print $2}' data.csv    # comma delimited
awk '{print $0}' file.txt          # $0 = the whole line
```

## My Terminal Output
```bash
rushi@rushi:~$ cat access.log
192.168.1.1 GET /index.html 200
192.168.1.2 POST /login 401
192.168.1.1 GET /about.html 200

rushi@rushi:~$ awk '{print $1}' access.log
192.168.1.1
192.168.1.2
192.168.1.1

rushi@rushi:~$ awk '{print $1, $4}' access.log
192.168.1.1 200
192.168.1.2 401
192.168.1.1 200

rushi@rushi:~$ awk -F',' '{print $2}' data.csv
age
22
25
```

## Field Reference
| Variable | Meaning |
|----------|---------|
| `$0` | The whole line |
| `$1` | First field |
| `$2` | Second field |
| `$NF` | Last field (however many there are) |

## Real pipeline example
```bash
# top 3 IPs hitting a server
awk '{print $1}' access.log | sort | uniq -c | sort -rn | head -3
```

## Key Points
- Fields are split by whitespace by default
- `-F` sets a custom delimiter: `-F','` for CSV, `-F':'` for passwd
- `$NF` gives the last field regardless of how many columns there are
- More flexible than `cut` when lines have variable spacing

## When I use this
Extracting IP addresses from access logs, pulling specific columns
from any structured text output, building log analysis pipelines.
