# grep — Find Matching Lines

## What it does
Searches for lines that match a pattern — the most used search
tool in Linux.

## Syntax
```bash
grep "ERROR" app.log           # lines containing ERROR
grep "timeout" *.log           # search across multiple files
grep -i error app.log          # case insensitive
grep -n error app.log          # show line numbers
grep -r TODO .                 # search whole folder tree
grep -v INFO app.log           # lines NOT matching
grep -c ERROR app.log          # count matching lines
```

## My Terminal Output
```bash
rushi@rushi:~$ grep ERROR server.log
ERROR disk full
ERROR timeout
ERROR disk full

rushi@rushi:~$ grep -c ERROR server.log
3

rushi@rushi:~$ grep -v ERROR server.log
INFO ok
WARN slow

rushi@rushi:~$ grep -n ERROR server.log
2:ERROR disk full
4:ERROR timeout
5:ERROR disk full
```

## Flags
| Flag | What it does |
|------|-------------|
| `-i` | Case insensitive match |
| `-n` | Show line numbers |
| `-r` | Search recursively through folders |
| `-v` | Invert — show lines that do NOT match |
| `-c` | Count matching lines |
| `-l` | Show only filenames that have matches |

## grep in pipelines
```bash
# filter then count
cat app.log | grep -i error | wc -l

# filter out noise
grep ERROR app.log | grep -v timeout

# find and rank
grep ERROR app.log | sort | uniq -c | sort -rn
```

## Key Points
- Pattern comes first, then the filename
- Wrap patterns in quotes to avoid shell expansion issues
- `-r` is very useful for searching config files across `/etc`
- `-v` strips out lines you do not want — great for noise removal

## When I use this
Finding errors in logs, searching config files, filtering pipeline
output down to only relevant lines.

