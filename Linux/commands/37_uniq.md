# uniq — Collapse Duplicate Lines

## What it does
Removes or counts adjacent duplicate lines.
Must be used on sorted input — uniq only removes consecutive duplicates.

## Syntax
```bash
sort access.log | uniq              # remove duplicates
sort access.log | uniq -c           # count each unique line
sort access.log | uniq -c | sort -rn  # rank by frequency
```

## My Terminal Output
```bash
rushi@rushi:~$ cat server.log
ERROR disk full
ERROR timeout
ERROR disk full

rushi@rushi:~$ sort server.log | uniq -c | sort -rn
      2 ERROR disk full
      1 ERROR timeout
      1 INFO ok
      1 WARN slow
```

## Flags
| Flag | What it does |
|------|-------------|
| `-c` | Prefix each line with its count |
| `-d` | Show only duplicate lines |
| `-u` | Show only unique lines (no duplicates) |

## Key Points
- Always sort before uniq — it only collapses ADJACENT duplicates
- `uniq -c` is the most useful flag — gives frequency count
- The classic pipeline: `sort | uniq -c | sort -rn` = rank by frequency
- This is the "top offenders" pattern used in real log analysis

## Classic pattern
```bash
grep ERROR app.log | sort | uniq -c | sort -rn | head -5
# most frequent errors, top 5
```

## When I use this
Counting how many times each error appears, finding the most
common IP in access logs, deduplicating any sorted list.
