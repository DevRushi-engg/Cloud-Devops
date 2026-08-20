# jobs, bg, fg — Background and Foreground Jobs

## What it does
Lets you run commands in the background while continuing to use
the terminal, and switch them back to the foreground.

## Syntax
```bash
sleep 100 &         # run in the background
jobs                # list background jobs in this shell
fg %1               # bring job 1 to the foreground
bg %1               # resume a paused job in the background
Ctrl+Z              # pause the current foreground job
Ctrl+C              # cancel the current foreground job
```

## My Terminal Output
```bash
rushi@rushi:~$ sleep 100 &
[1] 5678

rushi@rushi:~$ jobs
[1]+  Running    sleep 100 &

rushi@rushi:~$ fg %1
sleep 100
^Z
[1]+  Stopped    sleep 100

rushi@rushi:~$ bg %1
[1]+ sleep 100 &
```

## Key Points
- `&` at the end of any command sends it to the background
- `jobs` only shows jobs in the CURRENT shell session
- `Ctrl+Z` pauses (suspends) a job — it is not killed, just frozen
- `fg` without a number brings back the most recent job
- For long-running tasks that survive logout, use `nohup` or `tmux`

## When I use this
Running a long download or build in the background while continuing
other work in the same terminal.
