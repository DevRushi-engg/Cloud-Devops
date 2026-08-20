# systemctl — Control System Services

## What it does
Manages services (daemons) on modern Linux using systemd.
One tool to start, stop, restart, enable, and check any service.

## Syntax
```bash
sudo systemctl status nginx          # is it running?
sudo systemctl start nginx           # start it now
sudo systemctl stop nginx            # stop it now
sudo systemctl restart nginx         # stop then start
sudo systemctl reload nginx          # reload config without stopping
sudo systemctl enable nginx          # start on every boot
sudo systemctl disable nginx         # do not start on boot
sudo systemctl enable --now nginx    # enable AND start right now
```

## My Terminal Output
```bash
rushi@rushi:~$ sudo systemctl status nginx
● nginx.service - A high performance web server
     Loaded: loaded (/lib/systemd/system/nginx.service; enabled)
     Active: active (running) since Mon 2026-08-11 10:00:00 IST
    Process: 1234 ExecStart=/usr/sbin/nginx
   Main PID: 1234 (nginx)

rushi@rushi:~$ sudo systemctl enable --now nginx
Created symlink /etc/systemd/system/multi-user.target.wants/nginx.service
```

## start vs enable
| Command | Effect |
|---------|--------|
| `start` | Starts the service NOW only |
| `enable` | Starts automatically on FUTURE boots |
| `enable --now` | Does BOTH at once |

## Key Points
- `status` shows recent logs too — first place to look when something breaks
- `restart` applies config changes — use after editing config files
- `reload` is gentler — no downtime, but not all services support it
- Press `q` to exit the status view
- Services are called "units" in systemd terminology

## When I use this
Every time I install a new service, after editing config files,
and when debugging why something is not running.
