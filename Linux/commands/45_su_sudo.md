# su & sudo — Switch Users and Borrow Admin Rights

## What it does
`sudo` runs a single command as root then returns to normal.
`su` switches fully into another user's shell session.

## Syntax
```bash
sudo apt update              # run ONE command as root
sudo -i                      # drop into a full root shell
su devuser                   # switch to another user
su -                         # become root with root's environment
exit                         # leave the switched session
```

## My Terminal Output
```bash
rushi@rushi:~$ sudo apt update
[sudo] password for rushi:
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
...

rushi@rushi:~$ su devuser
Password:
devuser@rushi:/home/rushi$ whoami
devuser
devuser@rushi:/home/rushi$ exit
rushi@rushi:~$
```

## sudo vs su
| | `sudo` | `su` |
|-|--------|------|
| Scope | One command | Full session |
| Password | YOUR password | TARGET user's password |
| Audit trail | Yes — logged | Minimal |
| Safer for daily use | ✅ | Less so |

## Key Points
- `sudo` is safer — it logs every command run with it
- After entering your password, sudo remembers for ~15 minutes
- `sudo -i` or `sudo su` drops you into a full root shell — use carefully
- The sudo rules live in `/etc/sudoers` — edit with `visudo` only
- Members of the `sudo` group can use sudo on Ubuntu

## When I use this
`sudo` for almost everything admin-related.
`su devuser` to test what a specific user can and cannot do.
