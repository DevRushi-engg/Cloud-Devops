# whoami, id, who, w — User Identity Commands

## What it does
Shows who you are, your group memberships, and who else
is logged into the machine right now.

## Syntax
```bash
whoami          # your current username
id              # your UID, GID and all groups
who             # everyone logged in right now
w               # like who, plus what they are doing
```

## My Terminal Output
```bash
rushi@rushi:~$ whoami
rushi

rushi@rushi:~$ id
uid=1000(rushi) gid=1000(rushi) groups=1000(rushi),27(sudo),1001(devs)

rushi@rushi:~$ who
rushi    pts/0        2026-08-11 10:00 (:0)

rushi@rushi:~$ w
 10:05:01 up 1:23, 1 user, load average: 0.10
USER     TTY      FROM      LOGIN@   IDLE   WHAT
rushi    pts/0    :0        10:00    0.00s  w
```

## Key Points
- `whoami` is the quickest identity check
- `id` shows numeric UIDs and GIDs — useful for permission debugging
- `who` shows all active sessions on the machine
- `w` adds CPU load and what command each user is running
- Even services run as their own users (like `www-data`) for safety

## When I use this
Before running sudo commands, troubleshooting permission errors,
and checking who else is on a shared server.
