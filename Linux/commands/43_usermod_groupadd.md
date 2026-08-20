# usermod & groupadd — Modify Users and Create Groups

## What it does
`usermod` modifies an existing user account.
`groupadd` creates a new group.

## Syntax
```bash
sudo usermod -aG devs devuser      # add user to a group
sudo usermod -aG sudo devuser      # grant sudo access
groups devuser                     # check their groups
sudo groupadd devs                 # create a new group
cat /etc/group | tail              # see all groups
```

## My Terminal Output
```bash
rushi@rushi:~$ sudo groupadd devs
rushi@rushi:~$ sudo usermod -aG devs devuser
rushi@rushi:~$ groups devuser
devuser : devuser devs

rushi@rushi:~$ sudo usermod -aG sudo devuser
rushi@rushi:~$ groups devuser
devuser : devuser devs sudo
```

## Flags — usermod
| Flag | What it does |
|------|-------------|
| `-aG` | Append to a group — NEVER drop `-a` |
| `-s` | Change login shell |
| `-l` | Rename the user |

## ⚠️ Critical Warning
```bash
# CORRECT — appends to existing groups
sudo usermod -aG devs devuser

# DANGEROUS — replaces ALL existing groups
sudo usermod -G devs devuser
```
Forgetting `-a` wipes all the user's other groups instantly.
Always use `-aG` together.

## Key Points
- Log out and back in for new group membership to take effect
- `groups devuser` confirms membership without logging out
- `/etc/group` lists all groups and their members
- Give a folder to a group with `chown :devs foldername`

## When I use this
Granting a developer access to a shared folder, adding a user to
the sudo group for admin rights.
