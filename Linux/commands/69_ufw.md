# ufw — Uncomplicated Firewall

## What it does
Controls which network ports are open or blocked on your machine.
Ubuntu's simple frontend for managing firewall rules.

## Syntax
```bash
sudo ufw allow 22           # allow SSH
sudo ufw allow 80           # allow HTTP
sudo ufw allow 443          # allow HTTPS
sudo ufw deny 3306          # block MySQL from outside
sudo ufw enable             # turn the firewall on
sudo ufw disable            # turn it off
sudo ufw status             # show current rules
sudo ufw status verbose     # more detail
```

## My Terminal Output
```bash
rushi@rushi:~$ sudo ufw allow 22
Rules updated
Rules updated (v6)

rushi@rushi:~$ sudo ufw allow 80
Rules updated

rushi@rushi:~$ sudo ufw enable
Command may disrupt existing ssh connections. Proceed? (y|n) y
Firewall is active and enabled on system startup

rushi@rushi:~$ sudo ufw status
Status: active

To                Action      From
--                ------      ----
22                ALLOW       Anywhere
80                ALLOW       Anywhere
```

## Key Points
- ALWAYS allow port 22 BEFORE enabling ufw — or you lock yourself out
- `allow` opens a port, `deny` blocks it
- `enable` turns protection on and persists across reboots
- `status` shows exactly what is allowed and denied
- You can also allow by service name: `sudo ufw allow ssh`
- `sudo ufw allow from 192.168.1.0/24` allows a whole subnet

## Common ports to know
| Port | Service |
|------|---------|
| 22 | SSH |
| 80 | HTTP |
| 443 | HTTPS |
| 3306 | MySQL |
| 5432 | PostgreSQL |
| 6379 | Redis |

## When I use this
Securing a new cloud VM before making it public, opening ports
for a new service, blocking unwanted traffic.

