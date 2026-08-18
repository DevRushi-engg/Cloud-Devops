# Linux Filesystem Hierarchy (FHS)

## What it is
Everything in Linux lives under one single root directory: `/`
No drive letters like C: or D: — just one big tree.
Every distro follows the same standard layout.

## Key Directories
| Path | What lives there |
|------|----------------|
| `/` | Root of everything |
| `/home` | Personal folders, one per user |
| `/etc` | System configuration files |
| `/var` | Logs, caches, things that change (`/var/log`) |
| `/usr` | Installed programs and their files |
| `/bin` | Essential commands (ls, cp, cat) |
| `/tmp` | Temporary files — wiped on reboot |

## My Terminal Output
```bash
rushi@rushi:~$ ls /
bin  boot  dev  etc  home  lib  media  mnt  opt
proc  root  run  sbin  srv  sys  tmp  usr  var

rushi@rushi:~$ ls /etc | head
adduser.conf
apt
bash.bashrc
cron.d
default
environment
hosts
hostname
```

## Key Points
- `/etc` is where you will spend a lot of time editing config files
- `/var/log` is where you debug servers — app logs live here
- `/tmp` is safe to write temp files — but never rely on them surviving a reboot
- Curious what a folder is for? Just `ls` it

## When I use this
Every time I need to find a config file, check logs, or understand where something is installed.
