# Command Substitution — Capture Command Output Into a Variable

## What it does
Runs a command and stores its output in a variable for use later.
This is how scripts work with dynamic values like dates and counts.

## Syntax
```bash
today=$(date +%F)
echo "Today is $today"

files=$(ls | wc -l)
echo "There are $files files here"

hostname=$(hostname)
```

## My Terminal Output
```bash
rushi@rushi:~$ today=$(date +%F)
rushi@rushi:~$ echo "Today is $today"
Today is 2026-08-11

rushi@rushi:~$ files=$(ls | wc -l)
rushi@rushi:~$ echo "There are $files files here"
There are 7 files here
```

## Key Points
- Use `$(command)` — modern and nestable
- The older backtick syntax `` `command` `` does the same but is harder to read
- Output is captured as a string — leading/trailing whitespace is trimmed
- Perfect for timestamps in filenames: `backup_$(date +%F).tar.gz`
- You can nest substitutions: `$(echo $(date))`

## Real use in a backup script
```bash
#!/bin/bash
DEST="$HOME/backup_$(date +%F).tar.gz"
tar -czf "$DEST" "$HOME/practice"
echo "Backed up to $DEST"
```

## When I use this
Creating timestamped filenames, counting files, capturing
hostname or IP for log entries.
