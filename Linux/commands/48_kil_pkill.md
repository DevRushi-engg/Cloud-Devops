# kill, pkill, killall — Stop Processes

## What it does
Sends a signal to a process to stop it.
Default signal asks nicely — `-9` forces it with no cleanup.

## Syntax
```bash
kill 1234           # ask the process to stop (PID)
kill -9 1234        # force stop — last resort
pkill nginx         # stop by process name
killall nginx       # stop all processes with this name
```

## My Terminal Output
```bash
rushi@rushi:~$ ps aux | grep sleep
rushi   5678  0.0  0.0  sleep 100

rushi@rushi:~$ kill 5678
rushi@rushi:~$ ps aux | grep sleep
# process is gone

rushi@rushi:~$ pkill nginx
# all nginx processes stopped
```

## Common Signals
| Signal | Number | What it does |
|--------|--------|-------------|
| `SIGTERM` | 15 (default) | Ask politely to stop — allows cleanup |
| `SIGKILL` | 9 | Force stop immediately — no cleanup |
| `SIGHUP` | 1 | Reload config without stopping |

## Key Points
- Always try `kill PID` first — give the process a chance to clean up
- `-9` is a last resort — it can leave temp files and corrupt data
- `pkill` is convenient but kills ALL matching processes by name
- Use `ps aux | grep name` to confirm the process is gone after killing
- `kill -1 PID` (SIGHUP) tells many services to reload their config

## When I use this
Stopping a frozen application, killing a runaway process that is
eating CPU, reloading nginx config without downtime.
