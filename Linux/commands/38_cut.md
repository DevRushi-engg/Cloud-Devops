# cut — Extract Columns

## What it does
Pulls out specific columns or character ranges from each line.

## Syntax
```bash
cut -d',' -f1 data.csv      # first field, comma delimited
cut -d':' -f1 /etc/passwd   # first field, colon delimited
cut -c1-10 file.txt         # characters 1 to 10
cut -d' ' -f1,3 log.txt     # fields 1 and 3, space delimited
```

## My Terminal Output
```bash
rushi@rushi:~$ cat data.csv
name,age,city
rushi,22,nashik
alice,25,mumbai

rushi@rushi:~$ cut -d',' -f1 data.csv
name
rushi
alice

rushi@rushi:~$ cut -d',' -f1,3 data.csv
name,city
rushi,nashik
alice,mumbai
```

## Flags
| Flag | What it does |
|------|-------------|
| `-d` | Set the delimiter character |
| `-f` | Pick which field(s) to extract |
| `-c` | Cut by character position instead of field |

## Key Points
- `-d` and `-f` always go together for field-based cutting
- Fields are numbered from 1, not 0
- `-f1,3` gives fields 1 and 3; `-f1-3` gives fields 1 through 3
- Great for CSV files and simple column-based logs

## When I use this
Extracting usernames from `/etc/passwd`, pulling specific columns
from CSV files, grabbing IPs from log lines.
