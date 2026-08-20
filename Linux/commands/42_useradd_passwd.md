# useradd & passwd — Create Users and Set Passwords

## What it does
`useradd` creates a new user account.
`passwd` sets or changes a user's password.

## Syntax
```bash
sudo useradd -m devuser                    # create with home folder
sudo useradd -m -s /bin/bash devuser       # also set login shell
sudo passwd devuser                        # set another user's password
passwd                                     # change your own password
```

## My Terminal Output
```bash
rushi@rushi:~$ sudo useradd -m -s /bin/bash devuser
rushi@rushi:~$ id devuser
uid=1001(devuser) gid=1001(devuser) groups=1001(devuser)

rushi@rushi:~$ sudo passwd devuser
New password:
Retype new password:
passwd: password updated successfully
```

## Flags — useradd
| Flag | What it does |
|------|-------------|
| `-m` | Create the user's home directory |
| `-s` | Set the login shell (usually `/bin/bash`) |
| `-u` | Set a specific UID |

## Key Points
- Always use `-m` — without it no home folder is created
- A new user cannot log in until a password is set
- On Ubuntu, `adduser` (interactive) is friendlier than `useradd`
- Both commands need `sudo` — they modify the system

## Files changed
- `/etc/passwd` — user account info
- `/etc/shadow` — hashed passwords
- `/home/devuser/` — new home directory

## When I use this
Setting up new team members on a server, creating service accounts
for applications.
