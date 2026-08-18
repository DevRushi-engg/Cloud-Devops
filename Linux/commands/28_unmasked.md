# umask — Default Permission Mask

## What it does
Controls what permissions new files and folders get by default
when they are created.

## Syntax
```bash
umask           # check current mask
umask 0022      # set the mask
```

## My Terminal Output
```bash
rushi@rushi:~$ umask
0022

rushi@rushi:~$ touch newfile.txt
rushi@rushi:~$ ls -l newfile.txt
-rw-r--r-- 1 rushi rushi 0 Aug 11 newfile.txt
```

## How it works
- Full permissions for a file = 666 (no execute by default)
- umask 0022 subtracts → 666 - 022 = 644
- Full permissions for a folder = 777
- umask 0022 subtracts → 777 - 022 = 755

## Key Points
- 0022 is the standard default on most systems
- You rarely change umask directly
- Knowing it explains why fresh files are 644 and folders are 755
- Check yours with `umask` — a value of 0022 is normal

## When I use this
Understanding why newly created files have specific permissions without running chmod.
