# sort — Order Lines

## What it does
Sorts lines in a file or from a pipe — alphabetically by default.

## Syntax
```bash
sort names.txt          # alphabetical
sort -n nums.txt        # numeric order
sort -r names.txt       # reverse order
sort -u names.txt       # sort and remove duplicates
sort -rn counts.txt     # numeric reverse — highest first
```

## My Terminal Output
```bash
rushi@rushi:~$ cat names.txt
banana
apple
cherry
apple

rushi@rushi:~$ sort names.txt
apple
apple
banana
cherry

rushi@rushi:~$ sort -rn counts.txt
42 ERROR
10 WARN
3 INFO
```

## Flags
| Flag | What it does |
|------|-------------|
| `-n` | Sort numerically (2 before 10) |
| `-r` | Reverse the order |
| `-u` | Remove duplicates while sorting |
| `-rn` | Numeric + reverse — highest number first |

## Key Points
- Default sort is alphabetical — `10` comes before `2` without `-n`
- Always use `-n` when sorting numbers
- `-rn` is the classic "rank by count" flag combination
- `sort` is almost always paired with `uniq` in real pipelines

## When I use this
Ranking log error counts, sorting IP lists, ordering any text
output before passing to `uniq`.

