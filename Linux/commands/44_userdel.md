# userdel — Remove a User

## What it does
Removes a user account from the system.

## Syntax
```bash
sudo userdel devuser        # remove account, keep home folder
sudo userdel -r devuser     # remove account AND home folder
sudo groupdel devs          # remove a group
```

## My Terminal Output
```bash
rushi@rushi:~$ sudo userdel -r devuser
rushi@rushi:~$ id devuser
id: 'devuser': no such user

rushi@rushi:~$ ls /home
rushi
# devuser home folder is gone too
```

## Flags
| Flag | What it does |
|------|-------------|
| `-r` | Also delete their home directory and mail spool |

## Key Points
- Without `-r` the home folder stays on disk — sometimes useful
- `-r` is permanent — no undo
- `groupdel` removes a group the same way
- Clean up test users so they do not pile up on servers
- Check `who` and `w` before deleting — make sure they are not logged in

## When I use this
Removing test accounts after a lab, offboarding team members from
a shared server.
