# df & du — Disk Usage

## What it does
`df` shows free disk space per filesystem. `du` shows folder sizes.

## Syntax
```bash
df -h               # free space, human readable
du -sh practice     # total size of a folder
du -sh *            # size of everything in current directory
```

## My Terminal Output
```bash
rushi@rushi:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   12G   38G  24% /

rushi@rushi:~$ du -sh ~/practice
24K     /home/rushi/practice
```

## Key Points
- `df -h` is the first command to run when a server runs out of disk space
- `du -sh *` helps find which folder is eating the most space
- `-h` = human readable (KB, MB, GB instead of bytes)

## When I use this
When a server or container reports disk full errors.
