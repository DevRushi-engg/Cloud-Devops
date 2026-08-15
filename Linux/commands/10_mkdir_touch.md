# mkdir & touch — Create Directories and Files

## What it does
`mkdir` creates directories. `touch` creates empty files.

## Syntax
```bash
mkdir scripts                          # single folder
mkdir -p practice/logs/scripts         # nested folders in one go
mkdir -p ~/practice/{logs,scripts,configs}  # brace expansion

touch app.log                          # single file
touch error.log access.log             # multiple files at once
```

## My Terminal Output
```bash
rushi@rushi:~$ mkdir -p ~/practice/{logs,scripts,configs}
rushi@rushi:~$ ls ~/practice
configs  logs  scripts

rushi@rushi:~$ touch logs/app.log logs/error.log
rushi@rushi:~$ ls logs/
access.log  app.log  error.log
```

## Key Points
- `mkdir -p` creates parent folders automatically, no error if they already exist
- Brace expansion `{a,b,c}` creates multiple folders in one command
- `touch` on an existing file just updates its last modified timestamp
- Fastest way to scaffold a project structure

## When I use this
Setting up any new project folder structure from scratch.
