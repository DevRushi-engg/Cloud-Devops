# find — Locate Files by Rule

## What it does
Searches a directory tree for files matching rules like name, type, or size.
Works across the whole tree, not just the current folder.

## Syntax
```bash
find . -name "*.log"          # by filename pattern
find /etc -type d             # folders only
find /etc -type f             # files only
find . -name "app*"           # name starts with app
```

## My Terminal Output
```bash
rushi@rushi:~$ find ~/practice -name "*.log"
/home/rushi/practice/logs/app.log
/home/rushi/practice/logs/error.log
/home/rushi/practice/logs/access.log

rushi@rushi:~$ find /etc -type d | head -5
/etc
/etc/apt
/etc/apt/apt.conf.d
/etc/ssh
/etc/cron.d
```

## Flags
| Flag | What it does |
|------|-------------|
| `-name` | Match by filename or pattern |
| `-type f` | Files only |
| `-type d` | Directories only |
| `-size +1M` | Files larger than 1MB |

## Key Points
- `.` means start searching from current directory
- Always quote the pattern: `"*.log"` not `*.log` (shell expansion issue)
- The command you reach for when you think "where is that file?"

## When I use this
Finding all log files across a project, or locating a config file anywhere under `/etc`.
