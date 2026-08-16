# Redirection & Pipes — > >> |

## What it does
Controls where command output goes — to a file or into another command.

## Syntax
```bash
echo "hi" > out.txt          # write to file (overwrites)
echo "hi" >> out.txt         # append to file (adds to end)
cat app.log | wc -l          # pipe output into another command
```

## My Terminal Output
```bash
rushi@rushi:~/practice$ echo "line1" > logs/app.log
rushi@rushi:~/practice$ echo "line2" >> logs/app.log
rushi@rushi:~/practice$ cat logs/app.log
line1
line2

rushi@rushi:~/practice$ cat logs/app.log | wc -l
2
```

## Key Points
- `>` overwrites the file completely — be careful
- `>>` appends — safe to use on existing files
- `|` (pipe) sends output of one command as input to the next
- Pipes are the core of Linux power — you can chain as many as you want

## Example pipeline
```bash
history | awk '{print $2}' | sort | uniq -c | sort -rn | head
# shows your 10 most used commands
```

## When I use this
All the time — saving command output to files, filtering logs, chaining commands.
