# Redirection — > >> 2> 2>&1 

## What it does
Controls where command output and errors go — to files, from files,
or merged together.

## Syntax
```bash
echo "line one" > out.txt      # write stdout to file (overwrites)
echo "line two" >> out.txt     # append stdout to file
ls /nope 2> errors.txt         # write stderr to file
cmd > all.txt 2>&1             # stdout and stderr together
cmd 2> /dev/null               # throw errors away
sort < names.txt               # feed a file as input
sort < names.txt > sorted.txt  # input and output together
```

## My Terminal Output
```bash
rushi@rushi:~$ echo "line one" > out.txt
rushi@rushi:~$ echo "line two" >> out.txt
rushi@rushi:~$ cat out.txt
line one
line two

rushi@rushi:~$ ls /nope 2> errors.txt
rushi@rushi:~$ cat errors.txt
ls: cannot access '/nope': No such file or directory

rushi@rushi:~$ ls /home /nope > all.txt 2>&1
rushi@rushi:~$ cat all.txt
/home:
rushi
ls: cannot access '/nope': No such file or directory
```

## Redirection Reference
| Operator | What it does |
|----------|-------------|
| `>` | Write stdout to file — overwrites existing content |
| `>>` | Append stdout to file — safe on existing files |
| `2>` | Write stderr to file |
| `2>&1` | Send stderr to same place as stdout |
| `<` | Feed a file as stdin to a command |
| `/dev/null` | The black hole — discard anything sent here |

## Key Points
- `>` silently wipes an existing file — be careful
- `>>` is the safe version for log files and repeated appends
- `2>&1` must come AFTER `>` to work correctly
- `/dev/null` is useful to silence noisy error output in scripts

## When I use this
Saving command output to files, separating errors from normal output,
silencing expected errors in scripts.

