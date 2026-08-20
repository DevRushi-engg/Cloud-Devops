# top & htop — Live Process Monitor

## What it does
Shows a live, auto-refreshing view of all running processes.
Sorted by CPU usage by default — instant view of what is
hogging resources.

## Syntax
```bash
top             # built-in live monitor
htop            # friendlier colored version
```

## Install htop if missing
```bash
sudo apt install htop
```

## My Terminal Output (top)
```
top - 10:05:01 up 1:23, 1 user, load average: 0.10
Tasks: 120 total, 1 running, 119 sleeping
%Cpu(s): 2.0 us, 0.5 sy, 0.0 ni, 97.0 id
MiB Mem: 7850 total, 4200 free, 2100 used

  PID USER    %CPU %MEM  COMMAND
 1234 rushi    5.0  1.2  python3
  890 root     0.5  0.3  nginx
```

## top keyboard controls
| Key | What it does |
|-----|-------------|
| `q` | Quit |
| `k` | Kill a process — enter PID |
| `M` | Sort by memory usage |
| `P` | Sort by CPU usage |
| `1` | Show individual CPU cores |

## Key Points
- `top` is always available — no install needed
- `htop` has mouse support, color, and easier navigation
- Load average: 3 numbers = last 1, 5, 15 minutes
- A load average above your CPU core count means the system is busy
- `htop` lets you scroll and select processes with arrow keys

## When I use this
When a server feels slow — immediately check top to find what
is consuming resources.
