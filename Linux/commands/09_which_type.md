# which & type — Locate a Command

## What it does
Finds where a command lives on the system and how it resolves.

## Syntax
```bash
which python3
type ls
```

## My Terminal Output
```bash
rushi@rushi:~$ which python3
/usr/bin/python3

rushi@rushi:~$ type ls
ls is aliased to 'ls --color=auto'
```

## Key Points
- `which` shows the full path of the executable
- `type` tells you if it is a binary, alias, or shell built-in
- Use these when you get "command not found" or the wrong version runs

## When I use this
Debugging PATH issues or confirming which version of a tool is being used.
