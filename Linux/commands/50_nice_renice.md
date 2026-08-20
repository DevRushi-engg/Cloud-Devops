# nice & renice — Set Process Priority

## What it does
Controls how much CPU priority a process gets relative to others.
Higher nice value = lower priority = plays nicer with other processes.

## Syntax
```bash
nice -n 10 ./heavy.sh          # start with lower priority
sudo renice -n 5 -p 1234       # change a running process
```

## My Terminal Output
```bash
rushi@rushi:~$ nice -n 10 ./heavy.sh &
[1] 5678

rushi@rushi:~$ ps -o pid,ni,comm -p 5678
  PID  NI COMMAND
 5678  10 heavy.sh

rushi@rushi:~$ sudo renice -n 15 -p 5678
5678 (process ID) old priority 10, new priority 15
```

## Priority Scale
| Nice Value | Meaning |
|-----------|---------|
| `-20` | Highest priority — very greedy |
| `0` | Default priority |
| `10` | Lower priority — polite |
| `19` | Lowest priority — very nice |

## Key Points
- Higher number = nicer to others = gets less CPU
- Default nice value is `0`
- Only root can set negative nice values (higher priority than default)
- `renice` adjusts a process that is already running
- Use this for batch jobs and backups that should not slow the server

## When I use this
Running a CPU-intensive backup or build job without slowing down
other services on the same server.
