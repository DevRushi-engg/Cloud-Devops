# sudo — Borrow Admin Rights

## What it does
Runs a single command as the superuser (root).
Root can override any permission on the system.

## Syntax
```bash
sudo apt update
sudo chmod 600 /etc/secret.conf
sudo chown root:root /etc/hosts
```

## My Terminal Output
```bash
rushi@rushi:~$ cat /etc/shadow
cat: /etc/shadow: Permission denied

rushi@rushi:~$ sudo cat /etc/shadow
[sudo] password for rushi:
root:*:19000:0:99999:7:::
...
```

## Key Points
- You are asked for YOUR password, not root's password
- After entering it once, sudo remembers for ~15 minutes
- `sudo` only elevates the single command — not your whole session
- If you hit "Permission denied", sudo is often the answer — but ask why first
- `sudo -i` or `sudo su` drops you into a full root shell (use carefully)

## ⚠️ Be careful
- Double check the command before pressing Enter
- Root can delete system files with no warning
- If something feels wrong, `Ctrl+C` to cancel

## When I use this
Installing packages, editing system config files, fixing ownership issues.
