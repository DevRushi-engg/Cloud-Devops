# journalctl — Read Service Logs

## What it does
Reads logs from systemd's centralized journal.
Your first stop when a service will not start or is behaving oddly.

## Syntax
```bash
journalctl -u nginx             # logs for one service
journalctl -u nginx -f          # follow live logs
journalctl -u nginx --since "1 hour ago"   # recent only
journalctl -b                   # logs since last boot
journalctl -p err               # errors only
```

## My Terminal Output
```bash
rushi@rushi:~$ journalctl -u nginx -f
-- Logs begin at Mon 2026-08-11 09:00:00 IST --
Aug 11 10:00:01 rushi nginx[1234]: nginx: the configuration file test is successful
Aug 11 10:00:01 rushi systemd[1]: Started A high performance web server.
Aug 11 10:05:22 rushi nginx[1234]: 127.0.0.1 - GET / HTTP/1.1 200
```

## Flags
| Flag | What it does |
|------|-------------|
| `-u` | Filter to one service unit |
| `-f` | Follow live — like `tail -f` |
| `-b` | Show logs from current boot only |
| `-p err` | Show only errors |
| `--since` | Logs from a specific time onwards |

## Key Points
- `-u nginx` is the flag you will use most
- `-f` keeps updating in real time — `Ctrl+C` to stop
- When `systemctl status` shows a failure, `journalctl -u name` shows why
- Logs survive reboots unlike `/var/log` on some systems

## When I use this
Debugging why nginx or any service failed to start, monitoring
a service in real time after a config change.
